---
title: Azure 애플리케이션 제품 속성을 구성 하는 방법
description: 파트너 센터에서 Azure 응용 프로그램 제품에 대 한 속성을 구성 하는 방법에 대해 알아봅니다.
author: aarathin
ms.author: aarathin
ms.reviewer: dannyevers
ms.service: marketplace
ms.subservice: partnercenter-marketplace-publisher
ms.topic: how-to
ms.date: 11/06/2020
ms.openlocfilehash: 1414f2ce53d1764e788749fc2d225c56f624bcdc
ms.sourcegitcommit: 22da82c32accf97a82919bf50b9901668dc55c97
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/08/2020
ms.locfileid: "94370248"
---
# <a name="how-to-configure-your-azure-application-offer-properties"></a>Azure 애플리케이션 제품 속성을 구성 하는 방법

이 문서에서는 상업적 marketplace에서 Azure 애플리케이션 제품에 대 한 속성을 구성 하는 방법을 설명 합니다.

**속성** 페이지에서 제품 및 법적 계약서에 적용 되는 범주를 정의 합니다. 이 페이지의 제품에 대 한 완전 하 고 정확한 세부 정보를 제공 하 여 적절 하 게 표시 하 고 올바른 고객 집합에 제공 해야 합니다.

## <a name="select-a-category-for-your-offer"></a>제품에 대 한 범주를 선택 합니다.

**범주** 에서 **범주** 링크를 선택 하 고 제품을 적절 한 상업적 marketplace 검색 영역으로 그룹화 하기 위한 범주를 하나 이상 선택 합니다. 각 기본 및 보조 범주에 대해 최대 두 개의 하위 범주를 선택 합니다. 제안에 적용 되는 하위 범주가 없으면 **해당 없음** 을 선택 합니다.

## <a name="provide-terms-and-conditions"></a>사용 약관 제공

**법률** 에서 제품에 대 한 사용 약관을 제공 합니다. 다음 두 가지 옵션을 사용할 수 있습니다.

- [선택적 개정 함께 표준 계약 사용](#use-the-standard-contract)
- [사용자 고유의 사용 약관 사용](#use-your-own-terms-and-conditions)

표준 계약 및 선택적 개정에 대 한 자세한 내용은 [Microsoft 상용 marketplace에 대 한 표준 계약](standard-contract.md)을 참조 하세요. [표준 계약](https://go.microsoft.com/fwlink/?linkid=2041178) PDF를 다운로드할 수 있습니다 (팝업 차단이 해제 되어 있는지 확인).

### <a name="use-the-standard-contract"></a>표준 계약 사용

고객을 위한 조달 프로세스를 간소화 하 고 소프트웨어 공급 업체에 대 한 법적 복잡성을 줄이기 위해 Microsoft는 상업적 marketplace에서 제품에 사용할 수 있는 표준 계약을 제공 합니다. 표준 계약에 따라 소프트웨어를 제공 하는 경우 고객은 한 번만 읽고 동의 하면 되며 사용자 지정 사용 약관을 만들 필요가 없습니다.

1. **Microsoft의 상용 marketplace에 대 한 표준 계약 사용** 확인란을 선택 합니다.

   ![Microsoft의 상용 marketplace에 대 한 표준 계약 사용 확인란을 보여 줍니다.](partner-center-portal/media/use-standard-contract.png)

1. **확인** 대화 상자에서 **동의** 를 선택 합니다. 표시 하려면 위로 스크롤해야 할 수도 있습니다.
1. 계속하기 전에 **초안 저장** 을 선택합니다.

> [!NOTE]
> 상업적 marketplace에 대 한 표준 계약을 사용 하 여 제품을 게시 한 후에는 사용자 고유의 사용자 지정 약관을 사용할 수 없습니다. 선택적 개정를 사용 하는 표준 계약에 따라 또는 사용자의 사용 약관에 따라 솔루션을 제공 합니다.

### <a name="add-amendments-to-the-standard-contract-optional"></a>표준 계약에 개정 추가 (선택 사항)

사용할 수 있는 개정는 _유니버설_ 및 _사용자 지정_ 의 두 가지 종류가 있습니다.

#### <a name="add-universal-amendment-terms"></a>유니버설 수정 용어 추가

**Microsoft의 상용 marketplace에 대 한 표준 계약에 대 한 범용 수정 약관** 상자에 범용 수정 용어를 입력 합니다. 이 상자에는 문자를 개수 제한 없이 입력할 수 있습니다. 이러한 조건은 검색 및 구매 흐름 중에 AppSource, Azure Marketplace 및/또는 Azure Portal의 고객에게 표시됩니다.

#### <a name="add-one-or-more-custom-amendments"></a>하나 이상의 사용자 지정 개정 추가

1. **Microsoft의 상용 marketplace에 대 한 표준 계약에 대 한 사용자 지정 개정 조건** 에서 **사용자 지정 수정 단어 추가 (최대 10 개)** 링크를 선택 합니다.
1. **사용자 지정 수정 용어** 상자에 수정 용어를 입력 합니다.
1. **테 넌 트 id** 상자에 테 넌 트 id를 입력 합니다. 이러한 사용자 지정 약관에 대해 지정 하는 테 넌 트 Id와 연결 된 고객만 Azure Portal의 제품 구매 흐름에서 볼 수 있습니다.

   > [!TIP]
   > 테 넌 트 ID는 Azure에서 고객을 식별 합니다. 이 ID를 고객에 게 요청 하 고 [**https://portal.azure.com**](https://portal.azure.com)  >  **Azure Active Directory**  >  **속성** 으로 이동 하 여 찾을 수 있습니다. 디렉터리 ID 값은 테 넌 트 ID (예: `50c464d3-4930-494c-963c-1e951d15360e` )입니다. [내 Microsoft Azure 및 Office 365 테넌트 ID는 무엇인가요?](https://www.whatismytenantid.com/)에서 도메인 이름 URL을 사용하여 고객의 조직 테넌트 ID를 조회할 수도 있습니다.

1. **설명** 상자에 테 넌 트 ID에 대 한 간단한 설명을 입력 합니다 (선택 사항). 이 설명은 수정으로 대상으로 하는 고객을 식별 하는 데 도움이 됩니다.
1. 다른 테 넌 트 ID를 추가 하려면 **고객의 테 넌 트 Id 추가** 링크를 선택 하 고 3 단계와 4 단계를 반복 합니다. 최대 20 개의 테 넌 트 Id를 추가할 수 있습니다.
1. 다른 수정 용어를 추가 하려면 1-5 단계를 반복 합니다. 제품당 최대 10개의 사용자 지정 수정안 사용 약관을 제공할 수 있습니다.
1. 계속하기 전에 **초안 저장** 을 선택합니다.

### <a name="use-your-own-terms-and-conditions"></a>사용자 고유의 사용 약관 사용

표준 계약 대신 사용자 고유의 사용 약관을 제공 하도록 선택할 수 있습니다. 고객은 이 약관에 동의해야 제품을 사용할 수 있습니다.

1. **법적** 에서 **Microsoft의 상용 marketplace에 대 한 표준 계약 사용** 확인란의 선택을 취소 했는지 확인 합니다.
1. 사용 **약관** 상자에 최대 1만 문자 텍스트를 입력 합니다.

   > [!NOTE]
   > 더 긴 설명이 필요한 경우 사용 약관을 찾을 수 있는 위치를 가리키는 단일 웹 주소를 입력 합니다. 이는 고객에게 활성 링크로 표시됩니다.

1. 다음 탭을 계속 하기 전에 **초안 저장** 을 선택 합니다. 제품 목록.

## <a name="next-steps"></a>다음 단계

- [Azure 애플리케이션 제품 목록 정보를 구성 하는 방법](create-new-azure-apps-offer-listing.md)
