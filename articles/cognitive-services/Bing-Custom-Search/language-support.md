---
title: 언어 지원 - Bing Custom Search API
titleSuffix: Azure Cognitive Services
description: Bing Custom Search API에 지원되는 언어 및 지역 목록입니다.
services: cognitive-services
author: aahill
manager: nitinme
ms.service: cognitive-services
ms.subservice: bing-custom-search
ms.topic: conceptual
ms.date: 09/25/2018
ms.author: aahi
ms.openlocfilehash: 2579d24e1a1754e873c6591b6d86ec12dd0dfa60
ms.sourcegitcommit: 22da82c32accf97a82919bf50b9901668dc55c97
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/08/2020
ms.locfileid: "94367321"
---
# <a name="language-and-region-support-for-the-bing-custom-search-api"></a>Bing Custom Search API에 대한 언어 및 지역 지원

> [!WARNING]
> Bing Search API Cognitive Services에서 Bing Search 서비스로 이동 합니다. **2020 년 10 월 30 일부 터** [여기](https://aka.ms/cogsvcs/bingmove)에 설명 된 프로세스에 따라 Bing Search의 새 인스턴스를 프로 비전 해야 합니다.
> Cognitive Services를 사용 하 여 프로 비전 된 Bing Search API는 향후 3 년 동안 또는 기업계약 종료 될 때까지 먼저 발생 합니다.
> 마이그레이션 지침은 [Bing Search Services](https://aka.ms/cogsvcs/bingmigration)를 참조 하십시오.

Bing Custom Search API는 수십 개의 국가/지역을 지원하며, 이 중에는 둘 이상의 언어를 사용하는 국가/지역도 많습니다.

선택 사항이지만, 요청에서 결과를 가져올 지역/국가를 식별하는 [mkt](/rest/api/cognitiveservices-bingsearch/bing-custom-search-api-v7-reference#mkt) 쿼리 매개 변수를 지정해야 합니다. 선택적 쿼리 매개 변수 목록은 [쿼리 매개 변수](/rest/api/cognitiveservices-bingsearch/bing-custom-search-api-v7-reference#query-parameters)를 참조하세요.

`cc` 쿼리 매개 변수를 사용하여 국가/지역을 지정할 수 있습니다. 국가/지역을 지정하는 경우 `Accept-Language` 헤더를 사용하여 언어 코드도 하나 이상 지정해야 합니다. 지원 되는 언어는 국가/지역에 따라 다릅니다. 이러한 설정은 **시장** 테이블의 각 국가/지역에 대해 제공 됩니다.

`Accept-Language` 헤더 및 `setLang` 쿼리 매개 변수는 함께 사용할 수 없으므로 둘 다 지정하면 안 됩니다. 자세한 내용은 [Accept-Language](/rest/api/cognitiveservices-bingsearch/bing-custom-search-api-v7-reference#acceptlanguage)를 참조하세요.

## <a name="countriesregions"></a>국가/지역

|국가/지역|코드|
|-------|----|
|아르헨티나|AR|
|오스트레일리아|AU|
|오스트리아|AT|
|벨기에|BE|
|브라질|BR|
|Canada|CA|
|칠레|CL|
|덴마크|DK|
|핀란드|FI|
|프랑스|FR|
|독일|DE|
|홍콩 특별 행정구|HK|
|인도|IN|
|인도네시아|ID|
|이탈리아|IT|
|일본|JP|
|한국|KR|
|말레이시아|MY|
|멕시코|MX|
|네덜란드|NL|
|뉴질랜드|NZ|
|노르웨이|아니요|
|중국|CN|
|폴란드|PL|
|포르투갈|PT|
|필리핀|PH|
|러시아|RU|
|사우디아라비아|SA|
|남아프리카|ZA|
|스페인|ES|
|스웨덴|SE|
|스위스|CH|
|대만|TW|
|터키|TR|
|United Kingdom|GB|
|미국|US|


## <a name="markets"></a>시장

|국가/지역|언어|시장 코드|
|-------|--------|-----------|
|아르헨티나|스페인어|es-AR|
|오스트레일리아|영어|en-AU|
|오스트리아|독일어|de-AT|
|벨기에|네덜란드어|nl-BE|
|벨기에|프랑스어|fr-BE|
|브라질|포르투갈어|pt-BR|
|캐나다|영어|en-CA|
|캐나다|프랑스어|fr-CA|
|칠레|스페인어|es-CL|
|덴마크|덴마크어|da-DK|
|핀란드|핀란드어|fi-FI|
|프랑스|프랑스어|fr-FR|
|독일|독일어|de-DE|
|홍콩 특별행정구|중국어 번체|zh-HK|
|인도|영어|en-IN|
|인도네시아|영어|en-ID|
|이탈리아|이탈리아어|it-IT|
|일본|일본어|ja-JP|
|한국|한국어|en-US|
|말레이시아|영어|en-MY|
|멕시코|스페인어|es-MX|
|네덜란드|네덜란드어|nl-NL|
|뉴질랜드|영어|en-NZ|
|노르웨이|노르웨이어|no-NO|
|중국|중국어|zh-CN|
|폴란드|폴란드어|pl-PL|
|포르투갈|포르투갈어|pt-PT|
|필리핀|영어|en-PH|
|러시아|러시아어|ru-RU|
|사우디아라비아|아랍어|ar-SA|
|남아프리카 공화국|영어|en-ZA|
|스페인|스페인어|es-ES|
|스웨덴|스웨덴어|sv-SE|
|스위스|프랑스어|fr-CH|
|스위스|독일어|de-CH|
|대만|중국어 번체|zh-TW|
|터키|터키어|tr-TR|
|영국|영어|en-GB|
|미국|영어|ko-KR|
|미국|스페인어|es-US|