---
title: Azure Data Factory를 사용 하 여 Azure Machine Learning Studio (클래식) 모델 업데이트
description: Azure Data Factory 및 Azure Machine Learning Studio (클래식)를 사용 하 여 예측 파이프라인을 만드는 방법을 설명 합니다.
services: data-factory
documentationcenter: ''
author: djpmsft
ms.author: daperlov
manager: jroth
ms.reviewer: maghan
ms.service: data-factory
ms.workload: data-services
ms.topic: conceptual
ms.date: 07/16/2020
ms.openlocfilehash: 83950c2d3c5439886ff787b69d9da4d0c214de31
ms.sourcegitcommit: 829d951d5c90442a38012daaf77e86046018e5b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/09/2020
ms.locfileid: "87092544"
---
# <a name="update-azure-machine-learning-studio-classic-models-by-using-update-resource-activity"></a>리소스 업데이트 작업을 사용 하 여 Azure Machine Learning Studio (클래식) 모델 업데이트

[!INCLUDE[appliesto-adf-asa-md](includes/appliesto-adf-asa-md.md)]

이 문서는 기본 Azure Data Factory-Azure Machine Learning Studio (클래식) 통합 문서: [Azure Machine Learning Studio (클래식) 및 Azure Data Factory를 사용 하 여 예측 파이프라인 만들기](transform-data-using-machine-learning.md)를 보완 합니다. 수행하지 않았다면 이 문서를 읽기 전에 기본 문서를 검토하세요.

## <a name="overview"></a>개요
운영 화 Azure Machine Learning Studio (클래식) 모델 프로세스의 일부로 모델을 학습 하 고 저장 합니다. 그런 다음, 이를 예측 웹 서비스를 만드는 데 사용합니다. 그러면 웹 사이트, 대시보드 및 모바일 앱에서 웹 서비스를 사용할 수 있습니다.

Azure Machine Learning Studio (클래식)를 사용 하 여 만드는 모델은 일반적으로 정적이 지 않습니다. 새 데이터를 사용할 수 있는 경우 또는 API 소비자가 자체적인 데이터를 가진 경우 모델을 재학습해야 합니다. 

재학습은 자주 발생할 수 있습니다. Batch 실행 작업 및 리소스 업데이트 작업을 사용 하 여 Azure Machine Learning Studio (클래식) 모델을 다시 학습 하 고 Data Factory를 사용 하 여 예측 웹 서비스를 업데이트할 수 있습니다.

다음 그림에서는 학습 및 예측 웹 서비스 간의 관계를 보여 줍니다.

![웹 서비스](./media/update-machine-learning-models/web-services.png)

## <a name="azure-machine-learning-studio-classic-update-resource-activity"></a>Azure Machine Learning Studio (클래식) 리소스 업데이트 작업

다음 JSON 코드 조각은 Azure Machine Learning Studio (클래식) 일괄 처리 실행 작업을 정의 합니다.

```json
{
    "name": "amlUpdateResource",
    "type": "AzureMLUpdateResource",
    "description": "description",
    "linkedServiceName": {
        "type": "LinkedServiceReference",
        "referenceName": "updatableScoringEndpoint2"
    },
    "typeProperties": {
        "trainedModelName": "ModelName",
        "trainedModelLinkedServiceName": {
                    "type": "LinkedServiceReference",
                    "referenceName": "StorageLinkedService"
                },
        "trainedModelFilePath": "ilearner file path"
    }
}
```

| 속성                      | 설명                              | 필수 |
| :---------------------------- | :--------------------------------------- | :------- |
| name                          | 파이프라인의 작업 이름입니다.     | 예      |
| description                   | 작업이 어떤 일을 수행하는지 설명하는 텍스트입니다.  | 예       |
| type                          | Azure Machine Learning Studio (클래식) 리소스 업데이트 작업의 경우 활동 형식은  **AzureMLUpdateResource**입니다. | 예      |
| linkedServiceName             | UpdateResourceEndpoint 속성을 포함 하는 Azure Machine Learning Studio (클래식) 연결 된 서비스입니다. | 예      |
| trainedModelName              | 업데이트할 웹 서비스 실험의 학습된 모델 모듈의 이름입니다. | 예      |
| trainedModelLinkedServiceName | 업데이트 작업으로 업로드되는 ilearner 파일을 보유한 Azure Storage 연결된 서비스의 이름입니다. | 예      |
| trainedModelFilePath          | 업데이트 작업으로 업로드되는 ilearner 파일을 나타내는 trainedModelLinkedService의 상대 파일 경로입니다. | 예      |

## <a name="end-to-end-workflow"></a>엔드투엔드 워크플로

모델을 다시 학습하고 예측 웹 서비스를 업데이트하는 전체 프로세스에는 다음 단계가 포함됩니다.

- **일괄 처리 실행 작업**을 사용하여 **학습 웹 서비스**를 호출합니다. 학습 웹 서비스를 호출 하는 것은 [Azure Machine Learning Studio (클래식)를 사용 하 여 예측 파이프라인 만들기 및 Data Factory Batch 실행 작업](transform-data-using-machine-learning.md)에 설명 된 예측 웹 서비스를 호출 하는 것과 같습니다. 학습 웹 서비스의 출력은 예측 웹 서비스를 업데이트 하는 데 사용할 수 있는 iLearner 파일입니다.
- **리소스 업데이트 작업**을 통해 **예측 웹 서비스**의 **리소스 업데이트 엔드포인트**를 호출하여 새로운 학습된 모델을 통해 웹 서비스를 업데이트합니다.

## <a name="azure-machine-learning-studio-classic-linked-service"></a>Azure Machine Learning Studio (클래식) 연결 된 서비스

위에서 언급 한 종단 간 워크플로가 작동 하려면 두 개의 Azure Machine Learning Studio (클래식) 연결 된 서비스를 만들어야 합니다.

1. 학습 웹 서비스에 대 한 Azure Machine Learning Studio (클래식) 연결 된 서비스는이 연결 된 서비스는 [Azure Machine Learning Studio (클래식)를 사용 하 여 예측 파이프라인 만들기 및 Data Factory 일괄 처리 실행 작업](transform-data-using-machine-learning.md)에서 설명한 것과 같은 방식으로 일괄 처리 실행 작업에서 사용 됩니다. 차이점은 학습 웹 서비스의 출력은 iLearner 파일입니다 .이 파일은 리소스 업데이트 작업에서 예측 웹 서비스를 업데이트 하는 데 사용 됩니다.
2. 예측 웹 서비스의 업데이트 리소스 끝점에 대 한 Azure Machine Learning Studio (클래식) 연결 된 서비스입니다. 리소스 업데이트 작업에서 위의 단계에서 반환된 iLearner 파일을 사용하여 예측 웹 서비스를 업데이트하는 데 사용됩니다.

두 번째 Azure Machine Learning Studio (클래식) 연결 된 서비스의 경우 Azure Machine Learning Studio (클래식) 웹 서비스가 기존 웹 서비스 또는 새 웹 서비스인 경우 구성이 달라 집니다. 차이점은 다음 섹션에서 별도로 설명합니다.

## <a name="web-service-is-new-azure-resource-manager-web-service"></a>새 Azure Resource Manager 웹 서비스

웹 서비스가 Azure Resource Manager 엔드포인트를 노출하는 새로운 유형의 웹 서비스인 경우 두 번째 **기본이 아닌** 엔드포인트를 추가할 필요가 없습니다. 연결된 서비스의 **updateResourceEndpoint**는 다음 형식을 갖습니다.

```
https://management.azure.com/subscriptions/{subscriptionId}/resourceGroups/{resource-group-name}/providers/Microsoft.MachineLearning/webServices/{web-service-name}?api-version=2016-05-01-preview
```

[Azure Machine Learning Studio (클래식) 웹 서비스 포털](https://services.azureml.net/)에서 웹 서비스를 쿼리할 때 URL에서 자리 표시자에 대 한 값을 가져올 수 있습니다.

새 유형의 리소스 업데이트 엔드포인트에는 서비스 주체 인증이 필요합니다. 서비스 주체 인증을 사용하려면 Azure AD(Azure Active Directory)에 애플리케이션 엔터티를 등록하고, 웹 서비스가 속한 구독 또는 리소스 그룹의 **참가자** 또는 **소유자** 역할을 이 엔터티에 부여합니다. [서비스 주체를 만들고 Azure 리소스를 관리하기 위한 권한을 할당하는 방법](../active-directory/develop/howto-create-service-principal-portal.md)을 참조하세요. 연결된 서비스를 정의하는 데 사용되므로 다음 값을 적어둡니다.

- 애플리케이션 UI
- 애플리케이션 키
- 테넌트 ID

샘플 연결된 서비스 정의는 다음과 같습니다.

```json
{
    "name": "AzureMLLinkedService",
    "properties": {
        "type": "AzureML",
        "description": "The linked service for AML web service.",
        "typeProperties": {
            "mlEndpoint": "https://ussouthcentral.services.azureml.net/workspaces/0000000000000000  000000000000000000000/services/0000000000000000000000000000000000000/jobs?api-version=2.0",
            "apiKey": {
                "type": "SecureString",
                "value": "APIKeyOfEndpoint1"
            },
            "updateResourceEndpoint": "https://management.azure.com/subscriptions/{subscriptionId}/resourceGroups/{resource-group-name}/providers/Microsoft.MachineLearning/webServices/{web-service-name}?api-version=2016-05-01-preview",
            "servicePrincipalId": "000000000-0000-0000-0000-0000000000000",
            "servicePrincipalKey": {
                "type": "SecureString",
                "value": "servicePrincipalKey"
            },
            "tenant": "mycompany.com"
        }
    }
}
```

다음 시나리오는 보다 자세한 내용을 제공합니다. Azure Data Factory 파이프라인에서 Azure Machine Learning Studio (클래식) 모델을 다시 학습 하 고 업데이트 하는 예제를 포함 합니다.


## <a name="sample-retraining-and-updating-an-azure-machine-learning-studio-classic-model"></a>샘플: Azure Machine Learning Studio (클래식) 모델 재 학습 및 업데이트

이 섹션에서는 **Azure Machine Learning Studio (클래식) 일괄 처리 실행 작업** 을 사용 하 여 모델을 다시 학습 하는 샘플 파이프라인을 제공 합니다. 또한 파이프라인은 **Azure Machine Learning Studio (클래식) 리소스 업데이트 작업** 을 사용 하 여 점수 매기기 웹 서비스에서 모델을 업데이트 합니다. 섹션에서는 또한 모든 연결된 서비스, 데이터 세트 및 파이프라인에 대한 JSON 코드 조각 예제도 제공합니다.

### <a name="azure-blob-storage-linked-service"></a>Azure Blob Storage 연결된 서비스:
Azure Storage는 다음 데이터를 보관합니다.

* 학습 데이터. Azure Machine Learning Studio (클래식) 학습 웹 서비스에 대 한 입력 데이터입니다.
* iLearner 파일. Azure Machine Learning Studio (클래식) 학습 웹 서비스의 출력입니다. 이 파일은 업데이트 리소스 작업에 대한 입력이기도 합니다.

연결된 서비스의 샘플 JSON 정의는 다음과 같습니다.

```JSON
{
    "name": "StorageLinkedService",
    "properties": {
        "type": "AzureStorage",
        "typeProperties": {
            "connectionString": "DefaultEndpointsProtocol=https;AccountName=name;AccountKey=key"
        }
    }
}
```

### <a name="linked-service-for-azure-machine-learning-studio-classic-training-endpoint"></a>Azure Machine Learning Studio (클래식) 학습 끝점에 대 한 연결 된 서비스
다음 JSON 코드 조각은 학습 웹 서비스의 기본 끝점을 가리키는 Azure Machine Learning Studio (클래식) 연결 된 서비스를 정의 합니다.

```JSON
{
    "name": "trainingEndpoint",
    "properties": {
        "type": "AzureML",
        "typeProperties": {
            "mlEndpoint": "https://ussouthcentral.services.azureml.net/workspaces/xxx/services/--training experiment--/jobs",
            "apiKey": "myKey"
        }
    }
}
```

**Azure Machine Learning Studio (클래식)** 에서 다음을 수행 하 여 **Mlendpoint** 및 **apikey**에 대 한 값을 가져옵니다.

1. 왼쪽 메뉴에서 **웹 서비스** 를 클릭합니다.
2. 웹 서비스 목록에서 **학습 웹 서비스** 를 클릭합니다.
3. **API 키** 텍스트 상자 옆의 복사를 클릭합니다. 클립보드의 키를 Data Factory JSON 편집기에 붙여넣습니다.
4. **Azure Machine Learning Studio (클래식)** 에서 **BATCH 실행** 링크를 클릭 합니다.
5. **요청** 섹션에서 **요청 URI**를 복사하여 Data Factory JSON 편집기에 붙여넣습니다.

### <a name="linked-service-for-azure-machine-learning-studio-classic-updatable-scoring-endpoint"></a>Azure Machine Learning Studio (클래식) 업데이트 가능한 점수 매기기 끝점에 대 한 연결 된 서비스:
다음 JSON 코드 조각은 점수 매기기 웹 서비스의 업데이트 가능한 끝점을 가리키는 Azure Machine Learning Studio (클래식) 연결 된 서비스를 정의 합니다.

```JSON
{
    "name": "updatableScoringEndpoint2",
    "properties": {
        "type": "AzureML",
        "typeProperties": {
            "mlEndpoint": "https://ussouthcentral.services.azureml.net/workspaces/00000000eb0abe4d6bbb1d7886062747d7/services/00000000026734a5889e02fbb1f65cefd/jobs?api-version=2.0",
            "apiKey": "sooooooooooh3WvG1hBfKS2BNNcfwSO7hhY6dY98noLfOdqQydYDIXyf2KoIaN3JpALu/AKtflHWMOCuicm/Q==",
            "updateResourceEndpoint": "https://management.azure.com/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/Default-MachineLearning-SouthCentralUS/providers/Microsoft.MachineLearning/webServices/myWebService?api-version=2016-05-01-preview",
            "servicePrincipalId": "fe200044-c008-4008-a005-94000000731",
            "servicePrincipalKey": "zWa0000000000Tp6FjtZOspK/WMA2tQ08c8U+gZRBlw=",
            "tenant": "mycompany.com"
        }
    }
}
```

### <a name="pipeline"></a>파이프라인
파이프라인에는 **AzureMLBatchExecution** 및 **AzureMLUpdateResource**라는 두 활동이 있습니다. 일괄 처리 실행 작업에서는 학습 데이터를 입력으로 가져오고, iLearner 파일을 출력으로 생성합니다. 그런 다음 리소스 업데이트 작업에서 이 iLearner 파일을 가져오고, 이를 사용하여 예측 웹 서비스를 업데이트합니다.

```JSON
{
    "name": "LookupPipelineDemo",
    "properties": {
        "activities": [
            {
                "name": "amlBEGetilearner",
                "description": "Use AML BES to get the ileaner file from training web service",
                "type": "AzureMLBatchExecution",
                "linkedServiceName": {
                    "referenceName": "trainingEndpoint",
                    "type": "LinkedServiceReference"
                },
                "typeProperties": {
                    "webServiceInputs": {
                        "input1": {
                            "LinkedServiceName":{
                                "referenceName": "StorageLinkedService",
                                "type": "LinkedServiceReference"
                            },
                            "FilePath":"azuremltesting/input"
                        },
                        "input2": {
                            "LinkedServiceName":{
                                "referenceName": "StorageLinkedService",
                                "type": "LinkedServiceReference"
                            },
                            "FilePath":"azuremltesting/input"
                        }
                    },
                    "webServiceOutputs": {
                        "output1": {
                            "LinkedServiceName":{
                                "referenceName": "StorageLinkedService",
                                "type": "LinkedServiceReference"
                            },
                            "FilePath":"azuremltesting/output"
                        }
                    }
                }
            },
            {
                "name": "amlUpdateResource",
                "type": "AzureMLUpdateResource",
                "description": "Use AML Update Resource to update the predict web service",
                "linkedServiceName": {
                    "type": "LinkedServiceReference",
                    "referenceName": "updatableScoringEndpoint2"
                },
                "typeProperties": {
                    "trainedModelName": "ADFV2Sample Model [trained model]",
                    "trainedModelLinkedServiceName": {
                        "type": "LinkedServiceReference",
                        "referenceName": "StorageLinkedService"
                    },
                    "trainedModelFilePath": "azuremltesting/output/newModelForArm.ilearner"
                },
                "dependsOn": [
                    {
                        "activity": "amlbeGetilearner",
                        "dependencyConditions": [ "Succeeded" ]
                    }
                ]
            }
        ]
    }
}
```
## <a name="next-steps"></a>다음 단계
다른 방법으로 데이터를 변환하는 방법을 설명하는 다음 문서를 참조하세요.

* [U-SQL 작업](transform-data-using-data-lake-analytics.md)
* [Hive 작업](transform-data-using-hadoop-hive.md)
* [Pig 작업](transform-data-using-hadoop-pig.md)
* [MapReduce 작업](transform-data-using-hadoop-map-reduce.md)
* [Hadoop 스트리밍 작업](transform-data-using-hadoop-streaming.md)
* [Spark 작업](transform-data-using-spark.md)
* [.NET 사용자 지정 작업](transform-data-using-dotnet-custom-activity.md)
* [저장 프로시저 작업](transform-data-using-stored-procedure.md)
