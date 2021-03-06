---
title: Custom Vision이란?
titleSuffix: Azure Cognitive Services
description: Azure Custom Vision 서비스를 사용하여 Azure 클라우드에서 사용자 지정 AI 이미지 분류자 및 개체 탐지기를 빌드하는 방법을 알아봅니다.
services: cognitive-services
author: PatrickFarley
manager: nitinme
ms.service: cognitive-services
ms.subservice: custom-vision
ms.topic: overview
ms.date: 09/14/2020
ms.author: pafarley
ms.custom: cog-serv-seo-aug-2020
keywords: 이미지 인식, 이미지 식별자, 이미지 인식 앱, custom vision
ms.openlocfilehash: 47227a60b1ed45499afdb42fbc062abc5ae51ff9
ms.sourcegitcommit: 80b9c8ef63cc75b226db5513ad81368b8ab28a28
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90605504"
---
# <a name="what-is-custom-vision"></a>Custom Vision이란?

[!INCLUDE [TLS 1.2 enforcement](../../../includes/cognitive-services-tls-announcement.md)]

Azure Custom Vision은 이미지 인식 서비스입니다. 이를 통해 자체 이미지 식별자를 빌드, 배포 및 개선할 수 있습니다. 이미지 식별자는 시각적 특성에 따라 이미지에 레이블(클래스 또는 개체를 나타냄)을 적용합니다. [Computer Vision](https://docs.microsoft.com/azure/cognitive-services/computer-vision/home) 서비스와 달리 Custom Vision을 사용하면 레이블을 지정하고 이를 감지하도록 사용자 지정 모델을 학습시킬 수 있습니다.

## <a name="what-it-does"></a>수행하는 작업

Custom Vision Service는 기계 학습 알고리즘을 사용하여 이미지를 분석합니다. 개발자는 문제의 특성이 특징인 이미지와 부족한 이미지 그룹을 제출합니다. 이미지를 제출할 때 직접 레이블을 지정합니다. 그런 다음, 알고리즘에서 이 데이터를 학습하고 동일한 해당 이미지에서 자체적으로 테스트하여 정확도를 계산합니다. 알고리즘이 학습되면, 테스트하고 다시 학습한 후 이미지 인식 앱에서 사용하여 새 이미지를 분류할 수 있습니다. 모델 자체를 내보내서 오프라인에서 사용할 수도 있습니다.

### <a name="classification-and-object-detection"></a>분류 및 개체 검색

Custom Vision 기능을 두 가지로 나눌 수 있습니다. **이미지 분류**는 하나 이상의 레이블을 이미지에 적용합니다. **개체 감지**도 이와 비슷하지만, 적용된 레이블이 있는 이미지의 좌표를 반환합니다.

### <a name="optimization"></a>Optimization

Custom Vision 서비스는 이미지 간의 주요 차이점을 신속하게 인식하도록 최적화되었으므로 적은 양의 데이터로 모델을 프로토타입을 시작할 수 있습니다. 일반적으로 레이블당 50개의 이미지로 시작하는 것이 좋습니다. 그러나 이렇게 하면 서비스가 이미지의 미세한 차이를 검색하는 데 최적화되지 않습니다(예: 품질 보증 시나리오에서 작은 금 또는 패인 자국 검색).

또한 특정 주체 자료(예: 랜드마크 또는 소매 항목)가 있는 이미지에 최적화된 여러 종류의 Custom Vision 알고리즘 중에서 선택할 수 있습니다 자세한 내용은 [분류자 빌드](getting-started-build-a-classifier.md) 또는 [개체 탐지기 빌드](get-started-build-detector.md) 가이드를 참조하세요.

## <a name="what-it-includes"></a>포함되는 항목

Custom Vision Service는 네이티브 SDK 세트로는 물론 [Custom Vision 웹 사이트](https://customvision.ai/)의 웹 기반 인터페이스를 통해 제공됩니다. 인터페이스를 통하거나 둘 모두를 사용하여 모델을 만들고, 테스트하고, 학습할 수 있습니다.

![Chrome 브라우저 창의 Custom Vision 웹 사이트](media/browser-home.png)

## <a name="data-privacy-and-security"></a>데이터 개인 정보 보호 및 보안

모든 Cognitive Services와 마찬가지로 Custom Vision 서비스를 사용하는 개발자는 고객 데이터에 대한 Microsoft의 정책에 대해 알고 있어야 합니다. Microsoft Trust Center의 [Cognitive Services 페이지](https://www.microsoft.com/trustcenter/cloudservices/cognitiveservices)에서 자세히 알아보세요.

## <a name="next-steps"></a>다음 단계

[분류자 빌드](getting-started-build-a-classifier.md) 가이드에 따라 웹 포털에서 Custom Vision 사용을 시작하거나 [클라이언트 라이브러리 빠른 시작](quickstarts/image-classification.md)을 완료하여 코드에서 기본 시나리오를 구현합니다.
