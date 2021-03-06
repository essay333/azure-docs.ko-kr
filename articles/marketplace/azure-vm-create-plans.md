---
title: Azure Marketplace에서 virtual machine 제품에 대 한 계획 만들기
description: Azure Marketplace에서 가상 컴퓨터 제품에 대 한 계획을 만드는 방법에 대해 알아봅니다.
ms.service: marketplace
ms.subservice: partnercenter-marketplace-publisher
ms.topic: how-to
author: mingshen-ms
ms.author: mingshen
ms.date: 10/19/2020
ms.openlocfilehash: bc5e98484560fcc15e0ea3e289069c84687f158c
ms.sourcegitcommit: 4f4a2b16ff3a76e5d39e3fcf295bca19cff43540
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93040583"
---
# <a name="how-to-create-plans-for-a-virtual-machine-offer"></a>가상 컴퓨터 제품에 대 한 계획을 만드는 방법

파트너 센터의 동일한 제품 내에서 다양한 플랜 옵션을 제공할 수 있습니다. 제품에는 수익 화 대상 그룹, Azure 지역, 기능 또는 VM 이미지에 따라 달라질 수 있는 하나 이상의 계획 (이전의 SKU)이 필요 합니다.

각 제품에 대해 최대 100 요금제를 만들 수 있습니다. 최대 45 개는 개인 일 수 있습니다. [Microsoft 상업적 marketplace에서 비공개 제품](private-offers.md)의 비공개 요금제에 대해 자세히 알아보세요.

플랜이 만들어지면 **플랜 개요** 탭을 선택하여 다음 항목을 표시합니다.

- 플랜 이름
- 라이선스 모델
- 대상 그룹(퍼블릭 또는 프라이빗)
- 현재 게시 상태
- 사용 가능한 작업

**플랜 개요** 창에서 사용할 수 있는 작업은 플랜의 현재 상태에 따라 달라집니다.

- 플랜 상태가 초안인 경우 **초안 삭제** 를 선택합니다.
- 플랜 상태가 라이브로 게시되는 경우 **플랜 판매 중지** 또는 **프라이빗 대상 그룹 동기화** 를 선택합니다.

## <a name="create-a-new-plan"></a>새 플랜 만들기

위쪽에서 **새 플랜 만들기** 를 선택합니다. **새 플랜** 대화 상자가 표시됩니다.

**플랜 ID** 상자에서 이 제품의 각 플랜에 대한 고유한 플랜 ID를 만듭니다. 이 ID는 제품 웹 주소의 고객에게 표시됩니다. 소문자와 숫자, 대시 또는 밑줄과 최대 50자만 사용할 수 있습니다.

> [!NOTE]
> **만들기** 를 선택한 후에는 플랜 ID를 변경할 수 없습니다.

**플랜 이름** 상자에서 이 플랜에 대한 이름을 입력합니다. 이 이름은 제품 내에서 선택할 플랜을 결정할 때 고객에게 표시됩니다. 플랜 간의 차이를 명확하게 나타내는 고유한 이름을 만듭니다. 예를 들어 *종량제* , *BYOL* , *고급* 및 *엔터프라이즈* 플랜이 포함된 **Windows Server** 를 입력할 수 있습니다.

**만들기** 를 선택합니다.

## <a name="plan-setup"></a>플랜 설정

플랜 유형에 대한 상위 수준 구성을 설정하고, 다른 플랜의 기술 구성을 다시 사용할지 여부를 지정하고, 플랜을 사용할 수 있는 Azure 지역을 식별합니다. 여기서 선택한 항목에 따라 동일한 플랜에 대한 다른 창에 표시되는 필드가 결정됩니다.

### <a name="reuse-a-technical-configuration"></a>기술 구성 다시 사용

동일한 유형의 플랜이 둘 이상 있고 패키지가 동일한 경우 **이 플랜은 다른 플랜의 기술 구성을 다시 사용합니다.** 를 선택할 수 있습니다. 이 옵션을 사용하면 이 제품에 대해 동일한 유형의 다른 플랜 중 하나를 선택하고 해당 기술 구성을 다시 사용할 수 있습니다.

> [!NOTE]
> 다른 플랜의 기술 구성을 다시 사용하는 경우 전체 **기술 구성** 탭이 이 플랜에서 숨겨집니다. 향후의 업데이트를 포함하여 다른 플랜의 기술 구성 세부 정보도 이 플랜에 사용됩니다. 플랜이 게시된 후에는 이 설정을 변경할 수 없습니다.

### <a name="azure-regions"></a>Azure 지역

플랜은 하나 이상의 Azure 지역에서 사용할 수 있어야 합니다.

**Azure 글로벌** 옵션을 선택하여 상업용 마켓플레이스 통합이 있는 모든 Azure 글로벌 지역의 고객이 플랜을 사용할 수 있도록 합니다. 자세한 내용은 [지리적 가용성 및 통화 지원](marketplace-geo-availability-currencies.md)을 참조하세요.

**Azure Government** 옵션을 선택하여 [Azure Government](../azure-government/documentation-government-welcome.md) 지역에서 플랜을 사용할 수 있도록 합니다. 이 지역은 미국 연방, 주, 지방 또는 부족 단체의 고객뿐만 아니라 이러한 고객에게 서비스를 제공할 수 있는 파트너에게도 제어된 액세스를 제공합니다. 게시자는 규정 준수 제어, 보안 조치 및 모범 사례를 담당합니다. Azure Government는 물리적으로 격리된 데이터 센터 및 네트워크를 사용합니다(미국에만 있음).

[Azure Government](../azure-government/documentation-government-manage-marketplace-partners.md)에 게시하기 전에 특정 엔드포인트가 다를 수 있으므로 환경에서 플랜을 테스트하고 유효성을 검사합니다. 플랜을 설정하고 테스트하려면 [Microsoft Azure Government 평가판](https://azure.microsoft.com/global-infrastructure/government/request/) 페이지에서 평가판 계정을 요청합니다.

> [!NOTE]
> 플랜이 게시되고 특정 Azure 지역에서 사용할 수 있으면 해당 지역을 제거할 수 없습니다.

### <a name="azure-government-certifications"></a>Azure Government 인증

이 옵션은 이전 섹션에서 **Azure Government** 를 Azure 지역으로 선택한 경우에만 표시됩니다.

Azure Government 서비스는 특정 정부 규정 및 요구 사항이 적용되는 데이터를 처리합니다. 예를 들어 FedRAMP, NIST 800.171(DIB), ITAR, IRS 1075, DoD L4 및 CJIS가 있습니다. 관련 프로그램에 대한 인증을 알리기 위해 해당 프로그램을 설명하는 최대 100개의 링크를 제공할 수 있습니다. 이러한 링크는 프로그램의 목록에 직접 연결되는 링크이거나 사용자 고유의 웹 사이트에 있는 목록의 규정 준수에 대한 설명에 연결되는 링크일 수 있습니다. 이러한 링크는 Azure Government 고객에게만 표시됩니다.

계속하기 전에 **초안 저장** 을 선택합니다.

## <a name="plan-listing"></a>플랜 목록

이 섹션에서는 플랜에 대한 목록 세부 정보를 구성합니다. 이 창에는 동일한 제품의 다른 플랜과 다를 수 있는 특정 정보가 표시됩니다.

### <a name="plan-name"></a>플랜 이름

이 필드는 사용자가 계획을 만들 때 지정한 이름으로 자동으로 채워집니다. 이 이름은 Azure Marketplace에서 이 플랜의 제목으로 표시됩니다. 100자로 제한됩니다.

### <a name="plan-summary"></a>플랜 요약

제품이 아니라 플랜에 대한 간단한 요약을 제공합니다. 이 요약은 100자로 제한됩니다.

### <a name="plan-description"></a>플랜 설명

이 소프트웨어 플랜을 고유하게 만드는 요소를 설명하고, 제품 내 플랜 간의 차이점을 설명합니다. 제품이 아니라 플랜에 대해서만 설명합니다. 플랜 설명은 최대 2,000자까지 포함할 수 있습니다.

계속하기 전에 **초안 저장** 을 선택합니다.

## <a name="pricing-and-availability"></a>가격 책정 및 가용성

이 창에서 구성하는 항목은 다음과 같습니다.

- 이 플랜을 사용할 수 있는 시장 모든 요금제는 하나 이상의 [시장](marketplace-geo-availability-currencies.md)에서 사용할 수 있어야 합니다.
- 시간당 가격
- 플랜을 모든 사용자에게 표시할지, 아니면 특정 고객(프라이빗 대상 그룹)에게만 표시할지 여부

### <a name="markets"></a>시장

모든 플랜은 하나 이상의 시장에서 사용할 수 있어야 합니다. 이 플랜을 구매할 수 있는 모든 시장 위치에 대한 확인란을 선택합니다. (이러한 시장의 사용자는 제품을 ["플랜 설정"](#plan-setup) 섹션에서 선택한 모든 Azure 지역에 계속 배포할 수 있습니다.) **세금 납부** 단추는 Microsoft에서 사용자를 대신하여 판매세(sales tax)와 사용세(use tax)를 납부하는 국가/지역을 표시합니다. 중국에 게시하는 경우 *체험* 또는 *BYOL(사용자 라이선스 필요)* 플랜으로 제한됩니다.

플랜의 가격을 미국 달러(USD) 통화로 이미 설정했고 다른 시장 위치를 추가하는 경우 새 시장의 가격은 현재 환율에 따라 계산됩니다. 게시하기 전에 항상 각 시장의 가격을 검토합니다. 변경 내용이 저장되면 **가격 내보내기(xlsx)** 를 선택하여 가격 책정을 검토합니다.

시장을 제거하면 활성 배포를 사용하는 해당 시장의 고객은 새 배포를 만들거나 기존 배포를 강화할 수 없습니다. 기존 배포에는 영향을 주지 않습니다.

### <a name="pricing"></a>가격 책정

**라이선스 모델** 에 대해 **사용량 기반 월간 청구 플랜** 을 선택하여 이 플랜에 대한 가격 책정을 구성하거나, **사용자 라이선스 필요** 를 선택하여 고객이 기존 라이선스를 통해 이 플랜을 사용할 수 있도록 합니다.

사용량 기반 월간 청구 플랜의 경우 다음 세 가지 가격 책정 항목 옵션 중 하나를 사용합니다.

- **코어당** : 코어당 가격 책정(USD)을 제공합니다. Microsoft는 현재 환율을 사용하여 코어 크기별 가격 책정을 계산하고 현지 통화로 변환합니다.
- **코어 크기별** : 코어 크기별 가격 책정(USD)을 제공합니다. Microsoft는 현재 환율을 사용하여 가격 책정을 계산하고 현지 통화로 변환합니다.
- **지역/국가 및 코어 크기별** : 모든 시장에 대해 각 코어 크기에 대한 가격 책정을 제공합니다. 가격은 스프레드시트에서 가져올 수 있습니다.

> [!NOTE]
> 가격 책정 데이터를 내보낼 수 있도록 가격 책정 변경 내용을 저장합니다. 플랜의 시장 가격이 게시된 후에는 나중에 변경할 수 없습니다. 가격을 게시하기 직전에 가격이 적절한지 확인하려면 가격 책정 스프레드시트를 내보내고 각 시장의 가격을 검토합니다.

### <a name="free-trial"></a>평가판

한 달 또는 3 개월 또는 6 개월 *무료 평가판* 을 고객에 게 제공할 수 있습니다.

### <a name="visibility"></a>표시 유형

모든 사용자에게 표시되거나 미리 선택한 사용자에게만 표시되도록 각 플랜을 설계할 수 있습니다. Azure 구독 ID를 사용하여 제한된 대상 그룹의 멤버 자격을 할당합니다.

**공용** : 플랜이 모든 사용자에게 표시됩니다.

**프라이빗 대상** : 플랜이 미리 선택한 대상 그룹에만 표시되도록 합니다. 프라이빗 플랜으로 게시된 후에는 대상 그룹을 업데이트하거나 퍼블릭으로 변경할 수 있습니다. 퍼블릭 플랜으로 책정되면 퍼블릭으로 유지해야 하며, 프라이빗 플랜으로 다시 변경할 수 없습니다.

> [!NOTE]
> 프라이빗 또는 제한된 대상 그룹은 **미리 보기** 창에서 정의한 미리 보기 대상 그룹이 다릅니다. 미리 보기 대상 그룹은 Azure Marketplace에서 라이브로 게시되기 _전에_ 해당 제품에 액세스할 수 있습니다. 프라이빗 대상 그룹 선택은 특정 플랜에만 적용되지만, 미리 보기 대상 그룹은 유효성 검사를 위해 모든 프라이빗 및 퍼블릭 플랜을 볼 수 있습니다.

**제한된 대상 그룹(Azure 구독 ID)** : Azure 구독 ID를 사용하여 이 프라이빗 플랜에 액세스할 수 있는 대상 그룹을 할당합니다. 필요에 따라 할당한 각 Azure 구독 ID에 대한 설명을 포함시킵니다. CSV 스프레드시트를 가져오는 경우 수동으로 최대 10개의 구독 ID를 추가하거나 최대 20,000개의 ID를 추가할 수 있습니다. Azure 구독 ID는 GUID로 표시되며, 모든 문자는 소문자여야 합니다.

>[!Note]
>사설 제안은 클라우드 솔루션 공급자 프로그램 (CSP)의 대리점을 통해 설정 된 Azure 구독에서 지원 되지 않습니다.

### <a name="hide-a-plan"></a>플랜 숨기기

가상 머신이 다른 솔루션 템플릿 또는 관리형 애플리케이션을 통해 참조될 때만 간접적으로 사용되어야 하는 경우 이 확인란을 선택하여 가상 머신을 게시하지만 해당 가상 머신을 직접 검색하는 고객에게는 숨깁니다.

> [!NOTE]
> 숨겨진 플랜은 미리 보기 링크를 지원하지 않습니다.

계속하기 전에 **초안 저장** 을 선택합니다.

## <a name="technical-configuration"></a>기술 구성

이 플랜과 연결되는 이미지 및 기타 기술 속성을 제공합니다. 자세한 내용은 [VM 제품 목록 세부 정보 구성](azure-vm-create-listing.md)을 참조 하세요.

> [!NOTE]
> **플랜 설정** 탭에서 다른 플랜의 패키지를 다시 사용하도록 이 플랜을 구성한 경우 **기술 구성** 탭이 표시되지 않습니다.

### <a name="operating-system"></a>운영 체제

**운영 체제** 창에서 다음을 수행합니다.

- **운영 체제 제품군** 에 대해 **Windows** 또는 **Linux** 운영 체제를 선택합니다.
- **릴리스** 또는 **공급업체** 에 대해 Windows 릴리스 또는 Linux 공급업체를 선택합니다.
- **운영 체제 이름** 에 대해 친숙한 운영 체제 이름을 입력합니다. 이 이름은 고객에게 표시됩니다.

### <a name="recommended-vm-sizes"></a>권장되는 VM 크기

Azure Marketplace에 표시할 최대 6개의 추천 가상 머신 크기를 선택합니다.

### <a name="open-ports"></a>포트 열기

배포된 가상 머신에서 퍼블릭 또는 프라이빗 포트를 엽니다.

### <a name="storage-option-for-deployment"></a>배포용 스토리지 옵션

**디스크 배포 옵션** 에 대해 고객이 가상 머신에 사용할 수 있는 디스크 배포 유형을 선택합니다. 배포를 **관리 디스크 배포** 로만 제한하는 것이 좋습니다.

### <a name="properties"></a>속성

**가속화된 네트워킹 지원** 에 대해 VM에서 [가속화된 네트워킹](https://go.microsoft.com/fwlink/?linkid=2124513)을 지원하는지 여부를 선택합니다.

### <a name="generations"></a>세대

가상 컴퓨터를 생성 하는 데 사용 되는 가상 하드웨어를 정의 합니다. 고객의 요구에 따라 1 세대 VM, 2 세대 VM 또는 둘 다를 게시할 수 있습니다.

1. 새 제품을 만들 때 **생성 유형을** 선택 하 고 요청 된 이미지 세부 정보를 입력 합니다.

    :::image type="content" source="./media/create-vm/azure-vm-generations-image-details.png" alt-text="생성 드롭다운 상자의 뷰입니다.":::

2. 계획에 다른 세대를 추가 하려면 **생성 추가** 를 선택 합니다.

    :::image type="content" source="./media/create-vm/azure-vm-generations-add.png" alt-text="생성 드롭다운 상자의 뷰입니다.":::

    그런 다음 생성 세부 정보를 입력 합니다.

    :::image type="content" source="./media/create-vm/azure-vm-generations-details.png" alt-text="생성 드롭다운 상자의 뷰입니다.":::

    선택한 **생성 ID** 는 제품 URL 및 ARM 템플릿 (해당 하는 경우)의 고객에 게 표시 됩니다. 소문자, 영숫자, 대시 또는 밑줄만 사용 합니다. 게시 된 후에는 수정할 수 없습니다.

3. 이미 게시 된 1 세대를 포함 하는 기존 VM을 업데이트 하려면 **기술 구성** 페이지에서 세부 정보를 편집 하기만 하면 됩니다.

    :::image type="content" source="./media/create-vm/azure-vm-generations-updating.png" alt-text="생성 드롭다운 상자의 뷰입니다.":::

1 세대와 2 세대 기능 간의 차이점에 대 한 자세한 내용은 [Azure의 2 세대 vm에 대 한 지원](../virtual-machines/generation-2.md)을 참조 하세요.

### <a name="vm-images"></a>VM 이미지

가상 머신 이미지에 대한 디스크 버전과 SAS(공유 액세스 서명) URI를 제공합니다. 각 VM 이미지에 대해 최대 16개의 데이터 디스크를 추가합니다. 지정된 제출에서 플랜당 하나의 새 이미지 버전만 제공합니다. 이미지가 게시된 후에는 편집할 수 없지만 삭제할 수는 있습니다. 버전을 삭제하면 새 사용자와 기존 사용자가 모두 삭제된 버전의 새 인스턴스를 배포할 수 없습니다.

- **디스크 버전** : 제공하는 이미지의 버전입니다.
- **SAS URI** : 운영 체제 VHD가 저장된 Azure 스토리지 계정의 위치입니다. SAS URI를 가져오는 방법을 알아보려면 [VM 이미지에 대 한 공유 액세스 서명 URI 가져오기](azure-vm-get-sas-uri.md)를 참조 하세요.
- 데이터 디스크 이미지는 Azure 스토리지 계정에 저장된 VHD 공유 액세스 서명 URI이기도 합니다.
- 플랜에서 제출당 하나의 이미지만 추가합니다.

사용하는 운영 체제에 관계없이 솔루션에 필요한 최소 수의 데이터 디스크만 추가합니다. 배포 중에 고객은 이미지의 일부인 디스크를 제거할 수 없지만, 배포 중 또는 배포 후에 언제든지 디스크를 추가할 수 있습니다.

계속하기 전에 **초안 저장** 을 선택하고, **플랜 개요** 로 돌아갑니다.

## <a name="next-steps"></a>다음 단계

- [미리 보기 대상 추가](azure-vm-create-preview.md)
