---
title: Azure Event Grid의 사용자 지정 항목
description: Azure Event Grid의 사용자 지정 항목에 대해 설명 합니다.
ms.topic: conceptual
ms.date: 07/07/2020
ms.openlocfilehash: 8f48824989c8ec51b766385188ad99e9e59cf621
ms.sourcegitcommit: 829d951d5c90442a38012daaf77e86046018e5b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/09/2020
ms.locfileid: "86113788"
---
# <a name="custom-topics-in-azure-event-grid"></a>Azure Event Grid의 사용자 지정 항목
Event grid 토픽은 원본에서 이벤트를 전송 하는 끝점을 제공 합니다. 게시자는 Event Grid 항목을 만들고 이벤트 원본에 항목이 하나 필요한지 또는 둘 이상 필요한지 여부를 결정합니다. 항목은 관련 이벤트의 컬렉션에 사용됩니다. 특정 이벤트 형식에 응답하려면 구독자가 구독할 토픽을 결정합니다.

**사용자 지정 토픽** 은 응용 프로그램 및 타사 항목입니다. 사용자 지정 토픽을 만들거나 사용자 지정 토픽에 대한 액세스가 할당되면 구독에 사용자 지정 토픽이 표시됩니다. 

애플리케이션을 디자인할 때는 만들려는 토픽 수를 유연하게 결정할 수 있습니다. 규모가 많은 솔루션의 경우 **관련 이벤트의 각 범주**에 대 한 **사용자 지정 항목** 을 만듭니다. 사용자 계정을 수정하고 주문을 처리하는 것과 관련된 이벤트를 보내는 애플리케이션을 예로 들 수 있습니다. 이벤트 처리기가 이벤트의 두 범주 모두를 원할 가능성은 낮습니다. 두 개의 사용자 지정 토픽을 만들고 이벤트 처리기가 관심 있는 토픽을 구독할 수 있도록 하세요. 소규모 솔루션의 경우 모든 이벤트를 단일 토픽으로 전송할 수도 있습니다. 원하는 이벤트 유형에 대한 이벤트 구독자를 필터링할 수 있습니다.

## <a name="event-schema"></a>이벤트 스키마
이벤트 스키마에 대 한 자세한 개요는 [Azure Event Grid 이벤트 스키마](event-schema.md)를 참조 하세요. 사용자 지정 항목의 경우 이벤트 게시자는 **데이터** 개체를 확인 합니다. 최상위 수준 데이터에는 표준 리소스 정의 이벤트와 동일한 필드가 있어야 합니다.

```json
[
  {
    "topic": string,
    "subject": string,
    "id": string,
    "eventType": string,
    "eventTime": string,
    "data":{
      object-unique-to-each-publisher
    },
    "dataVersion": string,
    "metadataVersion": string
  }
]
```

다음 섹션에서는 Azure Portal, CLI, PowerShell 및 Azure Resource Manager (ARM) 템플릿을 사용 하 여 사용자 지정 항목을 만드는 자습서에 대 한 링크를 제공 합니다. 


## <a name="azure-portal-tutorials"></a>Azure Portal 자습서
|제목  |설명  |
|---------|---------|
| [빠른 시작: Azure Portal을 사용하여 사용자 지정 이벤트 만들기 및 라우팅](custom-event-quickstart-portal.md) | 포털을 사용하여 사용자 지정 이벤트를 전송하는 방법을 보여 줍니다. |
| [빠른 시작: Azure Queue Storage로 사용자 지정 이벤트 라우팅](custom-event-to-queue-storage.md) | Queue Storage에 사용자 지정 이벤트를 보내는 방법을 설명합니다. |
| [방법: 사용자 지정 토픽에 게시](post-to-custom-topic.md) | 사용자 지정 토픽에 이벤트를 게시하는 방법을 설명합니다. |


## <a name="azure-cli-tutorials"></a>Azure CLI 자습서
|제목  |설명  |
|---------|---------|
| [빠른 시작: Azure CLI를 사용하여 사용자 지정 이벤트 만들기 및 라우팅](custom-event-quickstart.md) | Azure CLI를 사용하여 사용자 지정 이벤트를 전송하는 방법을 보여 줍니다. |
| [Azure CLI: Event Grid 사용자 지정 토픽 만들기](./scripts/event-grid-cli-create-custom-topic.md)|사용자 지정 토픽을 만드는 샘플 스크립트입니다. 스크립트는 엔드포인트 및 키를 검색합니다.|
| [Azure CLI: 사용자 지정 토픽에 대한 이벤트 구독](./scripts/event-grid-cli-subscribe-custom-topic.md)|사용자 지정 토픽에 대한 구독을 만드는 샘플 스크립트입니다. WebHook에 이벤트를 보냅니다.|

## <a name="azure-powershell-tutorials"></a>Azure PowerShell 자습서
|제목  |설명  |
|---------|---------|
| [빠른 시작: Azure PowerShell을 사용하여 사용자 지정 이벤트 만들기 및 라우팅](custom-event-quickstart-powershell.md) | Azure PowerShell을 사용하여 사용자 지정 이벤트를 전송하는 방법을 보여 줍니다. |
| [PowerShell: Event Grid 사용자 지정 토픽 만들기](./scripts/event-grid-powershell-create-custom-topic.md)|사용자 지정 토픽을 만드는 샘플 스크립트입니다. 스크립트는 엔드포인트 및 키를 검색합니다.|
| [PowerShell: 사용자 지정 토픽에 대한 이벤트 구독](./scripts/event-grid-powershell-subscribe-custom-topic.md)|사용자 지정 토픽에 대한 구독을 만드는 샘플 스크립트입니다. WebHook에 이벤트를 보냅니다.|

## <a name="arm-template-tutorials"></a>ARM 템플릿 자습서
|제목  |설명  |
|---------|---------|
| [Resource Manager 템플릿: 토픽 및 WebHook 엔드포인트 사용자 지정](https://github.com/Azure/azure-quickstart-templates/tree/master/101-event-grid) | 사용자 지정 토픽 및 해당 사용자 지정 토픽에 대한 구독을 만드는 Resource Manager 템플릿입니다. WebHook에 이벤트를 보냅니다. |
| [Resource Manager 템플릿: 토픽 및 Event Hubs 엔드포인트 사용자 지정](https://github.com/Azure/azure-quickstart-templates/tree/master/101-event-grid-event-hubs-handler)| 사용자 지정 토픽에 대한 구독을 만드는 Resource Manager 템플릿입니다. Azure Event Hubs에 이벤트를 전송합니다. |

## <a name="next-steps"></a>다음 단계
다음 문서를 참조하세요. 

- [시스템 항목](system-topics.md)
- [도메인](event-domains.md)