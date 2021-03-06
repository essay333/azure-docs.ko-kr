---
title: 작업 영역 이란?
titleSuffix: Azure Machine Learning
description: 작업 영역은 Azure Machine Learning의 최상위 리소스입니다. 로그, 메트릭, 출력 및 스크립트의 스냅숏을 비롯 하 여 모든 학습 실행에 대 한 기록을 유지 합니다. 이 정보를 사용 하 여 최상의 모델을 생성 하는 학습 실행을 결정 합니다.
services: machine-learning
ms.service: machine-learning
ms.subservice: core
ms.topic: conceptual
ms.author: sgilley
author: sdgilley
ms.date: 09/22/2020
ms.openlocfilehash: 1076b49a101d5657397ef12b8fac672d37e477b0
ms.sourcegitcommit: 96918333d87f4029d4d6af7ac44635c833abb3da
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93324808"
---
# <a name="what-is-an-azure-machine-learning-workspace"></a>Azure Machine Learning 작업 영역이란?

작업 영역은 Azure Machine Learning의 최상위 리소스 이며 Azure Machine Learning를 사용할 때 만드는 모든 아티팩트를 사용할 수 있는 중앙 집중식 환경을 제공 합니다.  작업 영역에는 로그, 메트릭, 출력 및 스크립트의 스냅숏을 비롯 하 여 모든 학습 실행의 기록이 유지 됩니다. 이 정보를 사용하여 최고의 모델을 생성하는 학습 실행을 확인합니다.  

원하는 모델이 있으면 작업 영역에 등록 합니다. 그런 다음 등록 된 모델 및 점수 매기기 스크립트를 사용 하 여 Azure Container Instances, Azure Kubernetes Service에 배포 하거나 FPGA (필드 프로그래밍 가능 게이트 배열)에 REST 기반 HTTP 끝점으로 배포 합니다. 모델을 Azure IoT Edge 장치에 모듈로 배포할 수도 있습니다.

## <a name="taxonomy"></a>분류 

다음은 작업 영역의 분류 체계를 보여주는 다이어그램입니다.

[![작업 영역 분류](./media/concept-workspace/azure-machine-learning-taxonomy.png)](./media/concept-workspace/azure-machine-learning-taxonomy.png#lightbox)

다이어그램에는 작업 영역의 다음 구성 요소가 표시 됩니다.

+ 작업 영역에는 Azure Machine Learning를 실행 하는 데 필요한 Python 환경으로 구성 된 클라우드 리소스 [Azure Machine Learning 계산 인스턴스가](concept-compute-instance.md)포함 될 수 있습니다.

+ [사용자 역할](how-to-assign-roles.md) 을 사용 하면 작업 영역을 다른 사용자, 팀 또는 프로젝트와 공유할 수 있습니다.
+ [계산 대상은](concept-azure-machine-learning-architecture.md#compute-targets) 실험을 실행 하는 데 사용 됩니다.
+ 작업 영역을 만들 때 [연결 된 리소스도](#resources) 생성 됩니다.
+ [실험](concept-azure-machine-learning-architecture.md#experiments) 은 모델을 작성 하는 데 사용 하는 학습 실행입니다.  
+ [파이프라인](concept-azure-machine-learning-architecture.md#ml-pipelines) 은 모델을 학습 하 고 재 학습 하는 데 사용할 수 있는 워크플로입니다.
+ 데이터 [집합](concept-azure-machine-learning-architecture.md#datasets-and-datastores) 은 모델 학습 및 파이프라인 생성에 사용 하는 데이터를 관리 하는 데 도움이 됩니다.
+ 배포 하려는 모델이 있으면 등록 된 모델을 만듭니다.
+ 등록 된 모델 및 점수 매기기 스크립트를 사용 하 여 [배포 끝점](concept-azure-machine-learning-architecture.md#endpoints)을 만듭니다.

## <a name="tools-for-workspace-interaction"></a>작업 영역 상호 작용 도구

다음과 같은 방법으로 작업 영역과 상호 작용할 수 있습니다.

> [!IMPORTANT]
> 아래 표시 된 (미리 보기) 도구는 현재 공개 미리 보기로 제공 됩니다.
> 미리 보기 버전은 서비스 수준 계약 없이 제공되며 프로덕션 워크로드에는 권장되지 않습니다. 특정 기능이 지원되지 않거나 기능이 제한될 수 있습니다. 자세한 내용은 [Microsoft Azure Preview에 대한 추가 사용 약관](https://azure.microsoft.com/support/legal/preview-supplemental-terms/)을 참조하세요.

+ 웹에서:
    + [Azure Machine Learning studio ](https://ml.azure.com) 
    + [Azure Machine Learning 디자이너](concept-designer.md) 
+ [Python 용 AZURE MACHINE LEARNING SDK](/python/api/overview/azure/ml/intro?preserve-view=true&view=azure-ml-py)를 사용 하는 모든 python 환경에서
+ [R (미리 보기)에 대 한 AZURE MACHINE LEARNING SDK](https://azure.github.io/azureml-sdk-for-r/reference/index.html)를 사용 하는 모든 r 환경
+ Azure Machine Learning [CLI 확장](./reference-azure-machine-learning-cli.md) 을 사용 하 여 명령줄에서
+ [Azure Machine Learning VS Code 확장](how-to-manage-resources-vscode.md#workspaces)


## <a name="machine-learning-with-a-workspace"></a>작업 영역을 사용 하는 기계 학습

Machine learning 작업은 작업 영역에 대 한 아티팩트를 읽고 씁니다.

+ 실험을 실행 하 여 모델 학습-작업 영역에 실험 실행 결과를 기록 합니다.
+ 자동화 된 ML을 사용 하 여 모델 학습-작업 영역에 학습 결과를 기록 합니다.
+ 작업 영역에 모델을 등록 합니다.
+ 모델 배포-등록 된 모델을 사용 하 여 배포를 만듭니다.
+ 재사용 가능한 워크플로를 만들고 실행 합니다.
+ 실험, 파이프라인, 모델, 배포 등 기계 학습 아티팩트를 봅니다.
+ 모델 추적 및 모니터링

## <a name="workspace-management"></a>작업 영역 관리

또한 다음 작업 영역 관리 작업을 수행할 수 있습니다.

| 작업 영역 관리 작업   | 포털              | 스튜디오 | Python SDK/R SDK       | CLI        | VS 코드
|---------------------------|---------|---------|------------|------------|------------|
| 작업 영역 만들기        | **&check;**     | | **&check;** | **&check;** | **&check;** |
| 작업 영역 액세스 관리    | **&check;**   || |  **&check;**    ||
| 계산 리소스 만들기 및 관리    | **&check;**   | **&check;** | **&check;** |  **&check;**   ||
| 노트북 VM 만들기 |   | **&check;** | |     ||

> [!WARNING]
> Azure Machine Learning 작업 영역을 다른 구독으로 이동하거나 소유하는 구독을 새 테넌트로 이동하는 것은 지원되지 않습니다. 이렇게 하면 오류가 발생할 수 있습니다.

## <a name="create-a-workspace"></a><a name='create-workspace'></a> 작업 영역 만들기

작업 영역을 만드는 방법에는 여러 가지가 있습니다.  

* 지점 및 클릭 인터페이스에 대 한 [Azure Portal](how-to-manage-workspace.md?tabs=azure-portal#create-a-workspace) 를 사용 하 여 각 단계를 안내 합니다.
* [Python 용 AZURE MACHINE LEARNING SDK](how-to-manage-workspace.md?tabs=python#create-a-workspace) 를 사용 하 여 python 스크립트 또는 Jupiter 노트북에서 즉시 작업 영역 만들기
* 회사 보안 표준을 사용 하 여 만들기를 자동화 하거나 사용자 지정 해야 하는 경우 [Azure Resource Manager 템플릿](how-to-create-workspace-template.md) 또는 [Azure Machine Learning CLI](reference-azure-machine-learning-cli.md) 를 사용 합니다.
* Visual Studio Code에서 작업 하는 경우 [VS Code 확장](how-to-manage-resources-vscode.md#create-a-workspace)을 사용 합니다.

> [!NOTE]
> 작업 영역 이름은 대/소문자를 구분하지 않습니다.

## <a name="associated-resources"></a><a name="resources"></a> 연결 된 리소스

새 작업 영역을 만들면 작업 영역에서 사용되는 여러 Azure 리소스가 자동으로 생성됩니다.

+ [Azure Storage 계정](https://azure.microsoft.com/services/storage/): 작업 영역에 대 한 기본 데이터 저장소로 사용 됩니다.  Azure Machine Learning 계산 인스턴스와 함께 사용 되는 jupyter 노트북도 여기에 저장 됩니다. 
  
  > [!IMPORTANT]
  > 기본적으로 저장소 계정은 범용 v1 계정입니다. 작업 영역을 만든 후 [이를 범용 v2로 업그레이드할](../storage/common/storage-account-upgrade.md) 수 있습니다. 범용 v2로 업그레이드 한 후 저장소 계정에서 계층적 네임 스페이스를 사용 하도록 설정 하지 마세요.

  기존 Azure Storage 계정을 사용 하려면 premium 계정 (Premium_LRS 및 Premium_GRS)이 될 수 없습니다. 또한 계층적 네임 스페이스 (Azure Data Lake Storage Gen2에서 사용)를 가질 수 없습니다. Premium storage 또는 계층적 네임 스페이스는 작업 영역의 _기본_ 저장소 계정에서 지원 되지 않습니다. _기본이 아닌_ 저장소 계정이 포함 된 premium storage 또는 계층적 네임 스페이스를 사용할 수 있습니다.
  
+ [Azure Container Registry](https://azure.microsoft.com/services/container-registry/): 학습 중에 또는 모델을 배포할 때 사용 하는 docker 컨테이너를 등록 합니다. 비용을 최소화 하기 위해 ACR은 배포 이미지를 만들 때까지 **지연 로드** 됩니다.

+ [Azure 애플리케이션 Insights](https://azure.microsoft.com/services/application-insights/): 모델에 대 한 모니터링 정보를 저장 합니다.

+ [Azure Key Vault](https://azure.microsoft.com/services/key-vault/): 계산 대상에서 사용 하는 암호 및 작업 영역에 필요한 기타 중요 한 정보를 저장 합니다.

> [!NOTE]
> 대신 [ARM 템플릿을 사용 하 여](how-to-create-workspace-template.md) [Python SDK](how-to-manage-workspace.md?tabs=python#create-a-workspace), [R sdk](https://azure.github.io/azureml-sdk-for-r/reference/create_workspace.html)또는 Azure Machine Learning CLI를 사용 하 여 작업 영역을 만들 때 기존 Azure 리소스 인스턴스를 사용할 수 있습니다.

<a name="wheres-enterprise"></a>

## <a name="what-happened-to-enterprise-edition"></a>Enterprise edition의 변경 내용

9 월 2020 현재 Enterprise edition 작업 영역에서 사용할 수 있었던 모든 기능을 기본 버전 작업 영역 에서도 사용할 수 있습니다. 새 엔터프라이즈 작업 영역을 더 이상 만들 수 없습니다.  매개 변수를 사용 하는 모든 SDK, CLI 또는 Azure Resource Manager 호출은 `sku` 계속 작동 하지만 기본 작업 영역이 프로 비전 됩니다.

12 월 21 일부 터 모든 Enterprise Edition 작업 영역은 동일한 기능을 가진 기본 버전으로 자동 설정 됩니다. 이 프로세스 중에 가동 중지 시간이 발생 하지 않습니다. 2021 년 1 월 1 일에 Enterprise Edition은 공식적으로 사용이 중지 됩니다. 

두 버전에서 고객은 사용 되는 Azure 리소스의 비용을 담당 하며 Azure Machine Learning에 대 한 추가 요금을 지불할 필요가 없습니다. 자세한 내용은 [Azure Machine Learning 가격 책정 페이지](https://azure.microsoft.com/pricing/details/machine-learning/) 를 참조 하세요.

## <a name="next-steps"></a>다음 단계

Azure Machine Learning을 시작하려면 다음을 참조하세요.

+ [Azure Machine Learning 개요](overview-what-is-azure-ml.md)
+ [작업 영역 만들기 및 관리](how-to-manage-workspace.md)
+ [자습서: 개발 환경에서 Azure Machine Learning 시작](tutorial-1st-experiment-sdk-setup-local.md)
+ [자습서: 계산 인스턴스에서 첫 번째 ML 실험 만들기 시작](tutorial-1st-experiment-sdk-setup.md)
+ [자습서: R SDK를 사용 하 여 Azure Machine Learning 시작](tutorial-1st-r-experiment.md)
+ [자습서: 자동화된 Machine Learning을 사용하여 처음으로 분류 모델 만들어 보기](tutorial-first-experiment-automated-ml.md) 
+ [자습서: 디자이너를 사용하여 자동차 가격 예측](tutorial-designer-automobile-price-train-score.md)