---
title: Azure Management 클라이언트 라이브러리를 사용하여 Cognitive Services 리소스 만들기
titleSuffix: Azure Cognitive Services
description: Azure Management 클라이언트 라이브러리를 사용하여 Azure Cognitive Services 리소스를 만들고 관리합니다.
services: cognitive-services
keywords: 인지 서비스, 인지 인텔리전스, 인지 솔루션, AI 서비스
author: PatrickFarley
manager: nitinme
ms.service: cognitive-services
ms.topic: quickstart
ms.date: 09/14/2020
ms.author: pafarley
zone_pivot_groups: programming-languages-set-ten
ms.openlocfilehash: e8628d051db7f5066a81171567f6f7e54fb0ab97
ms.sourcegitcommit: 32c521a2ef396d121e71ba682e098092ac673b30
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91262453"
---
# <a name="quickstart-create-a-cognitive-services-resource-using-the-azure-management-client-library"></a>빠른 시작: Azure Management 클라이언트 라이브러리를 사용하여 Cognitive Services 리소스 만들기

이 빠른 시작을 사용하여 Azure Management 클라이언트 라이브러리를 통해 Azure Cognitive Services 리소스를 만들고 관리합니다.

Azure Cognitive Services는 REST API가 있는 클라우드 기반 서비스이며, 개발자가 직접적인 AI(인공 지능) 또는 데이터 과학 기술이나 지식 없이도 인지적 인텔리전스를 애플리케이션에 빌드하도록 지원하는 데 사용할 수 있는 클라이언트 라이브러리 SDK입니다. Azure Cognitive Services를 사용하는 개발자는 보고, 듣고, 말하고, 이해하고, 추론할 수도 있는 인지적 솔루션을 통해 애플리케이션에 인지적 기능을 손쉽게 추가할 수 있습니다.

개별 AI 서비스는 Azure 구독에서 만든 Azure [리소스](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)로 표시됩니다. 리소스를 만든 후 생성된 키와 엔드포인트를 사용하여 애플리케이션을 인증할 수 있습니다.

::: zone pivot="programming-language-csharp"

[!INCLUDE [C# SDK quickstart](includes/quickstarts/management-csharp.md)]

::: zone-end

::: zone pivot="programming-language-java"

[!INCLUDE [Java SDK quickstart](includes/quickstarts/management-java.md)]

::: zone-end

::: zone pivot="programming-language-javascript"

[!INCLUDE [NodeJS SDK quickstart](includes/quickstarts/management-node.md)]

::: zone-end

::: zone pivot="programming-language-python"

[!INCLUDE [Python SDK quickstart](includes/quickstarts/management-python.md)]

::: zone-end
