---
title: Azure Security Center의 새로운 기능 보관
description: 6개월 전 또는 그 이전의 Azure Security Center의 새로운 기능 및 변경된 기능에 대한 설명입니다.
services: security-center
documentationcenter: na
author: memildin
manager: rkarlin
ms.service: security-center
ms.devlang: na
ms.topic: conceptual
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/11/2020
ms.author: memildin
ms.openlocfilehash: e802f798ade5e6bfe0b40b17bbf15df5387ef7c3
ms.sourcegitcommit: 6a902230296a78da21fbc68c365698709c579093
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93357847"
---
# <a name="archive-for-whats-new-in-azure-security-center"></a>Azure Security Center의 새로운 기능 보관

기본 [Azure Security Center의 새로운 기능](release-notes.md) 릴리스 정보 페이지에는 지난 6개월 동안의 업데이트가 포함되어 있지만 이 페이지에는 더 오래된 항목도 포함되어 있습니다.

이 페이지에서는 다음에 대한 정보를 제공합니다.

- 새로운 기능
- 버그 수정
- 사용되지 않는 기능




## <a name="may-2020"></a>2020년 5월

5월의 업데이트는 다음과 같습니다.
- [중복된 경고 제거 규칙(미리 보기)](#alert-suppression-rules-preview)
- [공급되는 가상 머신 취약성 평가 일반 공급](#virtual-machine-vulnerability-assessment-is-now-generally-available)
- [JIT(just-in-Time) VM(가상 머신) 액세스의 변경 사항](#changes-to-just-in-time-jit-virtual-machine-vm-access)
- [사용자 지정 권장 사항이 별도의 보안 컨트롤로 이동됨](#custom-recommendations-have-been-moved-to-a-separate-security-control)
- [설정/해제가 컨트롤의 권장 사항 보기에 또는 단순 목록으로 추가됨](#toggle-added-to-view-recommendations-in-controls-or-as-a-flat-list)
- [확장된 보안 컨트롤 "보안 모범 사례 구현"](#expanded-security-control-implement-security-best-practices)
- [이제 일반 공급되는 사용자 지정 메타데이터가 포함된 사용자 지정 정책](#custom-policies-with-custom-metadata-are-now-generally-available)
- [파일리스 공격 탐지로 마이그레이션하는 크래시 덤프 분석 기능](#crash-dump-analysis-capabilities-migrating-to-fileless-attack-detection)


### <a name="alert-suppression-rules-preview"></a>중복된 경고 제거 규칙(미리 보기)

이 새로운 기능(현재 미리 보기 상태)은 경고 피로를 줄이는 데 도움이 됩니다. 규칙을 사용하여 조직 내 정상적인 작업에 무해하거나 관련이 있는 것으로 알려진 경고를 자동으로 숨깁니다. 이렇게 하면 가장 관련성이 높은 위협에 집중할 수 있습니다. 

활성화된 중복된 경고 제거 규칙과 일치하는 경고는 계속 생성되지만 해당 상태는 해제됨으로 설정됩니다. Azure Portal에서 상태를 보거나 Security Center 보안 경고에 액세스할 수 있습니다.

중복된 경고 제거 규칙은 경고를 자동으로 해제할 조건을 정의합니다. 일반적으로 다음과 같은 경우에는 중복된 경고 제거 규칙을 사용합니다.

- 거짓 긍정으로 식별한 경고를 표시 안 함

- 너무 자주 트리거되는 경고를 표시 안 함

[Azure Security Center의 위협 방지에서 경고 표시 안 함](alerts-suppression-rules.md)에 대해 자세히 알아보세요.


### <a name="virtual-machine-vulnerability-assessment-is-now-generally-available"></a>공급되는 가상 머신 취약성 평가 일반 공급

가상 머신에 대한 통합 취약성 평가가 이제 Security Center의 표준 계층에 추가 비용 없이 포함됩니다. 이 확장은 Qualys에서 제공하지만 검색 결과를 다시 Security Center에 보고합니다. Qualys 라이선스 또는 Qualys 계정이 필요하지 않습니다. 모든 항목이 Security Center 내에서 원활하게 처리됩니다.

새 솔루션은 가상 머신을 지속적으로 스캔하여 취약성을 찾고 Security Center에 검색 결과를 제공할 수 있습니다. 

솔루션을 배포하려면 새 보안 권장 사항을 사용합니다.

"가상 머신에서 기본 제공 취약성 평가 솔루션 사용(Qualys에서 제공)"

[가상 머신에 대한 Security Center의 통합 취약성 평가](deploy-vulnerability-assessment-vm.md#overview-of-the-integrated-vulnerability-scanner)에 대해 자세히 알아보세요.



### <a name="changes-to-just-in-time-jit-virtual-machine-vm-access"></a>JIT(just-in-Time) VM(가상 머신) 액세스의 변경 사항

Security Center에는 VM의 관리 포트를 보호하는 선택적 기능이 포함되어 있습니다. 이는 가장 일반적인 형태의 무차별 암호 대입 공격에 대한 방어를 제공합니다.

이 업데이트는 이 기능을 다음과 같이 변경합니다.

- VM에서 JIT를 사용하도록 설정하라는 권장 사항의 이름이 변경되었습니다. 이전의 "가상 머신에서 Just-In-Time 네트워크 액세스 제어를 적용해야 함"은 이제 다음과 같습니다. "가상 머신의 관리 포트는 Just-In-Time 네트워크 액세스 제어로 보호해야 함".

- 추천 사항은 열린 관리 포트가 있는 경우에만 트리거됩니다.

[JIT 액세스 기능](security-center-just-in-time.md)에 대해 자세히 알아보세요.


### <a name="custom-recommendations-have-been-moved-to-a-separate-security-control"></a>사용자 지정 권장 사항이 별도의 보안 컨트롤로 이동됨

향상된 보안 점수와 함께 도입된 보안 제어 중 하나는 "보안 모범 사례 구현"이었습니다. 구독에 대해 생성된 사용자 지정 권장 사항은 자동으로 해당 컨트롤에 배치되었습니다. 

사용자 지정 권장 사항을 더 쉽게 찾을 수 있도록 이를 전용 보안 컨트롤인 "사용자 지정 권장 사항"으로 이동했습니다. 이 컨트롤은 보안 점수에 영향을 미치지 않습니다.

[Azure Security Center에서 향상된 보안 점수(미리 보기)](secure-score-security-controls.md)의 보안 컨트롤에 대해 자세히 알아보세요.


### <a name="toggle-added-to-view-recommendations-in-controls-or-as-a-flat-list"></a>설정/해제가 컨트롤의 권장 사항 보기에 또는 단순 목록으로 추가됨

보안 컨트롤은 관련된 보안 권장 사항의 논리적 그룹입니다. 취약한 공격 노출 영역을 반영합니다. 컨트롤은 이러한 권장 사항을 구현하는 데 도움이 되는 지침을 포함하는 보안 권장 사항 집합입니다.

조직이 각 개별 공격 노출 영역을 얼마나 잘 보호하고 있는지 즉시 확인하려면 각 보안 컨트롤의 점수를 검토합니다.

기본적으로 권장 사항은 보안 컨트롤에 표시됩니다. 이 업데이트에서는 목록으로 표시할 수도 있습니다. 영향을 받는 리소스의 상태를 기준으로 정렬된 간단한 목록으로 표시하려면 새 ' 컨트롤 그룹화' 토글을 사용합니다. 토글은 포털의 목록 상단에 있습니다.

보안 컨트롤 및 이 토글은 새로운 보안 점수 환경의 일부입니다. 포털 내에서 사용자 의견을 보내 주시기 바랍니다.

[Azure Security Center에서 향상된 보안 점수(미리 보기)](secure-score-security-controls.md)의 보안 컨트롤에 대해 자세히 알아보세요.

:::image type="content" source="./media/secure-score-security-controls/recommendations-group-by-toggle.gif" alt-text="추천 사항에 대한 제어를 기준으로 그룹화 설정/해제":::

### <a name="expanded-security-control-implement-security-best-practices"></a>확장된 보안 컨트롤 "보안 모범 사례 구현" 

향상된 보안 점수와 함께 도입된 보안 제어 중 하나는 "보안 모범 사례 구현"입니다. 이 컨트롤에 권장 사항이 있으면 보안 점수에 영향을 주지 않습니다. 

이 업데이트를 사용하면 세 가지 권장 사항이 원래 배치된 컨트롤에서 이 모범 사례 제어로 이동했습니다. 이러한 세 가지 권장 사항에 대한 위험이 처음에 생각된 것보다 낮은 것으로 판단했기 때문에 이 단계를 수행했습니다.

또한 이 컨트롤에는 두 가지 새로운 권장 사항이 도입되어 추가되었습니다.

이동한 세 가지 권장 사항은 다음과 같습니다.

- **구독에 대한 읽기 권한이 있는 계정에서 MFA를 사용하도록 설정해야 합니다** (원래 "MFA 사용" 컨트롤).
- **읽기 권한이 있는 외부 계정을 구독에서 제거해야 합니다** (원래 "액세스 및 권한 관리" 컨트롤).
- **구독에 대해 최대 3명의 소유자를 지정해야 합니다** (원래 "액세스 및 권한 관리" 컨트롤).

컨트롤에 추가된 두 가지 새로운 권장 사항은 다음과 같습니다.

- **Windows Virtual Machines에 게스트 구성 확장을 설치해야 함(미리 보기)** - [Azure Policy 게스트 구성](../governance/policy/concepts/guest-configuration.md)을 사용하면 가상 머신 내에서 서버 및 애플리케이션 설정에 대한 가시성을 제공합니다(Windows만 해당).

- **Windows Defender Exploit Guard를 머신에서 사용하도록 설정해야 함(미리 보기)** - Windows Defender Exploit Guard는 Azure Policy 게스트 구성 에이전트를 활용합니다. Exploit Guard에는 다양한 공격 벡터에 대해 디바이스를 잠그고 맬웨어 공격에서 일반적으로 사용되는 동작을 차단하면서 기업에서 보안 위험과 생산성 요구 사항 사이의 균형을 맞출 수 있도록 설계된 4가지 구성 요소가 있습니다(Windows에만 해당).

[Exploit Guard 정책 만들기 및 배포](/mem/configmgr/protect/deploy-use/create-deploy-exploit-guard-policy)에서 Windows Defender Exploit Guard에 대해 자세히 알아보세요.

[향상된 보안 점수(미리 보기)](secure-score-security-controls.md)의 보안 제어에 대해 자세히 알아보세요.



### <a name="custom-policies-with-custom-metadata-are-now-generally-available"></a>이제 일반 공급되는 사용자 지정 메타데이터가 포함된 사용자 지정 정책

사용자 지정 정책은 이제 Security Center 권장 사항 환경, 보안 점수 및 규정 준수 표준 대시보드의 일부입니다. 이 기능은 이제 일반 공급되며, Security Center에서 조직의 보안 평가 적용 범위를 확장할 수 있습니다. 

Azure 정책에서 사용자 지정 이니셔티브를 만들고, 여기에 정책을 추가하고 Azure Security Center에 온보딩하고, 권장 사항으로 시각화합니다.

이제 사용자 지정 권장 구성 메타데이터를 편집하는 옵션도 추가했습니다. 메타데이터 옵션에는 심각도, 수정 단계, 위협 정보 등이 포함됩니다.  

[세부 정보를 사용하여 사용자 지정 권장 사항 향상](custom-security-policies.md#enhance-your-custom-recommendations-with-detailed-information)에 대해 자세히 알아보세요.



### <a name="crash-dump-analysis-capabilities-migrating-to-fileless-attack-detection"></a>파일리스 공격 탐지로 마이그레이션하는 크래시 덤프 분석 기능 

Microsoft는 CDA(Windows 크래시 덤프 분석) 탐지 기능을 [파일리스 공격 탐지](defender-for-servers-introduction.md#what-are-the-benefits-of-azure-defender-for-servers)에 통합하고 있습니다. 파일리스 공격 탐지 분석은 Windows 컴퓨터에 대해 다음과 같은 보안 경고의 향상된 버전을 제공합니다. 코드 주입 검색됨, 모조 Windows 모듈 탐지됨, Shellcode 검색됨 및 의심스러운 코드 세그먼트 탐지됨.

이러한 전환의 이점 중 일부는 다음과 같습니다.

- **사전 예방적이고 시기 적절한 맬웨어 탐지** - 작동 중단이 발생할 때까지 기다린 다음, 분석을 실행하여 악성 아티팩트를 찾는 데 관련된 CDA 접근 방법입니다. 파일리스 공격 탐지를 사용하면 실행되는 동안 메모리 내 위협이 사전 예방적으로 식별됩니다. 

- **보강 경고** - 파일리스 공격 탐지의 보안 경고에는 CDA에서 사용할 수 없는 강화(예: 활성 네트워크 연결 정보)가 포함됩니다. 

- **경고 집계** - CDA는 단일 크래시 덤프 내에서 여러 공격 패턴을 탐지한 경우 여러 보안 경고를 트리거했습니다. 파일리스 공격 탐지는 동일한 프로세스에서 식별된 모든 공격 패턴을 단일 경고로 결합하여 여러 경고를 상호 연결할 필요가 없도록 합니다.

- **Log Analytics 작업 영역에 대한 요구 사항 감소** - 잠재적으로 중요한 데이터가 포함된 크래시 덤프는 Log Analytics 작업 영역에 더 이상 업로드되지 않습니다.






## <a name="april-2020"></a>2020년 4월

4월의 업데이트는 다음과 같습니다.
- [이제 일반 공급되는 동적 규정 준수 패키지](#dynamic-compliance-packages-are-now-generally-available)
- [이제 Azure Security Center 무료 계층에 포함되는 ID 권장 사항](#identity-recommendations-now-included-in-azure-security-center-free-tier)


### <a name="dynamic-compliance-packages-are-now-generally-available"></a>이제 일반 공급되는 동적 규정 준수 패키지

Azure Security Center 규제 준수 대시보드에는 이제 추가 산업 및 규제 표준을 추적하는 **동적 규정 준수 패키지** (현재 일반 공급)가 포함되어 있습니다.

Security Center 보안 정책 페이지에서 구독 또는 관리 그룹에 동적 규정 준수 패키지를 추가할 수 있습니다. 표준 또는 벤치 마크를 온보딩하면 규정 준수 대시보드에 평가로 매핑된 모든 관련 준수 데이터가 포함된 표준이 표시됩니다. 온보딩된 표준에 대한 요약 보고서는 다운로드할 수 있습니다.

이제 다음과 같은 표준을 추가할 수 있습니다.

- **NIST SP 800-53 R4**
- **SWIFT CSP CSCF-v2020**
- **영국 공식 및 영국 NHS**
- **캐나다 연방 PBMM**
- **Azure CIS 1.1.0(신규)** (Azure CIS 1.1.0을 보다 완벽하게 표현)

또한 최근 일반 준수 프레임워크를 기반으로 하는 보안 및 규정 준수 모범 사례에 대해 Microsoft에서 작성한 Azure 관련 지침인 **Azure 보안 벤치마크** 를 추가했습니다. 추가 표준은 사용할 수 있게 되면 대시보드에서 지원될 예정입니다.  
 
[규정 준수 대시보드의 표준 집합 사용자 지정](update-regulatory-compliance-packages.md)에 대해 자세히 알아보세요.


### <a name="identity-recommendations-now-included-in-azure-security-center-free-tier"></a>이제 Azure Security Center 무료 계층에 포함되는 ID 권장 사항

Azure Security Center 무료 계층에 대한 ID 및 액세스에 대한 보안 권장 사항이 이제 일반 공급됩니다. 이는 CSPM(클라우드 보안 상태 관리) 기능을 무료로 제공하는 노력의 일부입니다. 지금까지 이러한 권장 사항은 표준 가격 책정 계층에서만 사용할 수 있었습니다.

ID 및 액세스 권장 사항의 예는 다음과 같습니다.

- "구독에 대한 소유자 권한이 있는 계정에 대해 다단계 인증을 사용하도록 설정해야 합니다."
- "구독에 대해 최대 3명의 소유자를 지정해야 합니다."
- "더 이상 사용되지 않는 계정은 구독에서 제거해야 합니다."

무료 가격 책정 계층에 대한 구독이 있는 경우 해당 보안 점수는 ID 및 액세스 보안에 대해 평가하지 않았기 때문에 이 변경의 영향을 받습니다.

[ID 및 액세스 권장 사항](recommendations-reference.md#recs-identity)에 대해 자세히 알아보세요.

[ID 및 액세스 모니터링](security-center-identity-access.md)에 대해 자세히 알아보세요.



## <a name="march-2020"></a>2020년 3월

3 월의 업데이트는 다음과 같습니다.

- [이제 일반 공급되는 워크플로 자동화](#workflow-automation-is-now-generally-available)
- [Windows Admin Center와 Azure Security Center 통합](#integration-of-azure-security-center-with-windows-admin-center)
- [Azure Kubernetes Service에 대한 보호](#protection-for-azure-kubernetes-service)
- [Just-in-Time 환경 개선](#improved-just-in-time-experience)
- [사용되지 않는 웹 애플리케이션에 대한 두 가지 보안 권장 사항](#two-security-recommendations-for-web-applications-deprecated)


### <a name="workflow-automation-is-now-generally-available"></a>이제 일반 공급되는 워크플로 자동화

Azure Security Center의 워크플로 자동화 기능이 이제 일반 공급됩니다. 이를 사용하여 보안 경고 및 권장 사항에 대한 Logic Apps를 자동으로 트리거합니다. 또한 빠른 수정 옵션을 사용할 수 있는 경고 및 모든 권장 사항에 대해 수동 트리거를 사용할 수 있습니다.

모든 보안 프로그램에는 인시던트 응답을 위한 여러 워크플로가 포함되어 있습니다. 이러한 프로세스에는 관련 이해 관계자에게 알리고, 변경 관리 프로세스를 시작하고, 특정 수정 단계를 적용하는 것이 포함될 수 있습니다. 보안 전문가는 가능한 한 해당 절차의 여러 단계를 자동화할 것을 권장합니다. 자동화는 오버헤드를 줄이고 프로세스 단계가 미리 정의된 요구 사항에 따라 빠르고 일관되게 수행되도록 하여 보안을 향상시킬 수 있습니다.

워크플로를 실행하기 위한 자동 및 수동 Security Center 기능에 대한 자세한 내용은 [워크플로 자동화](workflow-automation.md)를 참조하세요.

[Logic Apps 만들기](../logic-apps/logic-apps-overview.md)에 대해 자세히 알아보세요.


### <a name="integration-of-azure-security-center-with-windows-admin-center"></a>Windows Admin Center와 Azure Security Center 통합

이제 Windows Admin Center에서 Azure Security Center로 온-프레미스 Windows 서버를 바로 이동할 수 있습니다. 그러면 Security Center는 온-프레미스 서버, 가상 머신 및 추가 PaaS 워크로드를 포함하여 모든 Windows Admin Center 리소스에 대한 보안 정보를 볼 수 있는 단일 창이 됩니다.

Windows Admin Center에서 Azure Security Center로 서버를 이동한 후 다음을 수행할 수 있습니다.

- Windows Admin Center의 Security Center 확장에서 보안 경고 및 권장 사항을 확인합니다.
- 보안 상태를 확인하고 Azure Portal 또는 API를 통해 Security Center에서 Windows Admin Center 관리 서버에 대한 추가 세부 정보를 검색합니다.

[Windows Admin Center와 Azure Security Center를 통합하는 방법](windows-admin-center-integration.md)에 대해 자세히 알아보세요.


### <a name="protection-for-azure-kubernetes-service"></a>Azure Kubernetes Service에 대한 보호

Azure Security Center는 AKS(Azure Kubernetes Service)를 보호하기 위해 컨테이너 보안 기능을 확장하고 있습니다.

널리 사용되는 오픈 소스 플랫폼 Kubernetes는 이제 컨테이너 오케스트레이션에 대한 업계 표준으로 널리 채택되고 있습니다. 이러한 광범위한 구현에도 불구하고, Kubernetes 환경을 보호하는 방법에 대한 이해가 부족합니다. 컨테이너화된 애플리케이션의 공격 노출 영역을 방어하려면 인프라가 안전하게 구성되고 잠재적 위협에 대해 지속적으로 모니터링되도록 하는 전문 지식이 필요합니다.

Security Center 방어에는 다음이 포함됩니다.

- **검색 및 가시성** - Security Center에 등록된 구독 내에서 관리되는 AKS 인스턴스를 지속적으로 검색합니다.
- **보안 권장 사항** - AKS에 대한 보안 모범 사례를 준수하는 데 도움이 되는 실행 가능한 권장 사항입니다. 이러한 권장 사항은 조직의 보안 상태의 일부로 표시되도록 보안 점수에 포함됩니다. AKS 관련 권장 사항의 예는 "역할 기반 액세스 제어를 사용하여 Kubernetes 서비스 클러스터에 대한 액세스를 제한해야 합니다"를 참조하세요.
- **위협 방지** - AKS 배포에 대한 지속적인 분석을 통해 Security Center는 호스트 및 AKS 클러스터 수준에서 탐지된 위협 및 악의적인 활동을 경고합니다.

[Security Center와 Azure Kubernetes Services 통합](defender-for-kubernetes-introduction.md)에 대해 자세히 알아보세요.

[Security Center의 컨테이너 보안 기능](container-security.md)에 대해 자세히 알아보세요.


### <a name="improved-just-in-time-experience"></a>Just-in-Time 환경 개선

관리 포트를 보호하는 Azure Security Center의 Just-in-Time 도구의 기능, 작업 및 UI는 다음과 같이 향상되었습니다. 

- **양쪽 맞춤 필드** - Azure Portal의 Just-in-Time 페이지를 통해 VM(가상 머신)에 대한 액세스를 요청할 때 새 선택적 필드를 사용하여 요청에 대한 근거를 입력할 수 있습니다. 이 필드에 입력한 정보는 활동 로그에서 추적할 수 있습니다. 
- **중복된 JIT(Just-in-Time) 규칙 자동 정리** - JIT 정책을 업데이트할 때마다 정리 도구가 자동으로 실행되어 전체 규칙 집합의 유효성을 검사합니다. 이 도구는 정책의 규칙과 NSG의 규칙 간 불일치를 검색합니다. 정리 도구에서 불일치를 발견하면 원인을 확인하고 안전한 경우 더 이상 필요하지 않은 기본 제공 규칙을 제거합니다. 클리너는 만든 규칙을 삭제하지 않습니다. 

[JIT 액세스 기능](security-center-just-in-time.md)에 대해 자세히 알아보세요.


### <a name="two-security-recommendations-for-web-applications-deprecated"></a>사용되지 않는 웹 애플리케이션에 대한 두 가지 보안 권장 사항

사용되지 않는 웹 애플리케이션에 대한 두 가지 보안 권장 사항은 다음과 같습니다. 

- IaaS NSG의 웹 애플리케이션에 대한 규칙을 강화해야 합니다.
    (관련 정책: IaaS의 웹 애플리케이션에 대한 NSG 규칙을 강화해야 합니다.)

- App Services에 대한 액세스를 제한해야 합니다.
    (관련 정책: App Services에 대한 액세스를 제한해야 합니다[미리 보기].)

이러한 권장 사항은 Security Center 권장 사항 목록에 더 이상 표시되지 않습니다. 관련 정책은 "Security Center 기본값"이라는 이니셔티브에 더 이상 포함되지 않습니다.

[보안 권장 사항](recommendations-reference.md)에 대해 자세히 알아보세요.




## <a name="february-2020"></a>2020년 2월

### <a name="fileless-attack-detection-for-linux-preview"></a>Linux에 대한 파일리스 공격 탐지(미리 보기)

공격자가 더 은밀한 방법을 사용하여 탐지를 방지하려고 함에 따라 Azure Security Center는 Windows 뿐만 아니라 Linux에 대한 파일리스 공격 탐지 기능을 확장하고 있습니다. 파일리스 공격은 소프트웨어 취약성을 이용하고, 악성 페이로드를 무해한 시스템 프로세스에 주입하며 메모리에 숨습니다. 이러한 기술은 다음과 같습니다.

- 디스크에서 맬웨어 추적 최소화 또는 제거
- 디스크 기반 맬웨어 검색 솔루션으로 검색 가능성을 크게 줄임

이 위협에 대처하기 위해 Azure Security Center는 2018년 10월에 파일리스 공격 탐지 기능을 릴리스했으며, Linux에 대해서도 파일리스 공격 탐지 기능을 확장했습니다. 



## <a name="january-2020"></a>2020년 1월

### <a name="enhanced-secure-score-preview"></a>보안 점수 향상(미리 보기)

이제 Azure Security Center의 향상된 버전의 보안 점수 기능이 미리 보기에서 제공됩니다. 이 버전에서 여러 권장 사항은 취약한 공격 노출 영역을 더 잘 반영하는 보안 컨트롤로 그룹화되어 있습니다(예: 관리 포트에 대한 액세스 제한).

미리 보기 단계에서 보안 점수 변경을 숙지하고 환경을 보다 안전하게 보호하는 데 도움이 되는 다른 수정을 결정합니다.

[향상 된 보안 점수 (미리 보기)](secure-score-security-controls.md)에 대해 자세히 알아보세요.



## <a name="november-2019"></a>2019년 11월

11 월의 업데이트는 다음과 같습니다.
 - [북아메리카 지역에서 Azure Key Vault에 대 한 위협 방지 (미리 보기)](#threat-protection-for-azure-key-vault-in-north-america-regions-preview)
 - [Azure Storage에 대한 위협 방지에 맬웨어 평판 차단 포함](#threat-protection-for-azure-storage-includes-malware-reputation-screening)
 - [Logic Apps로 워크플로 자동화(미리 보기)](#workflow-automation-with-logic-apps-preview)
 - [대량 리소스에 대한 빠른 수정 일반 공급](#quick-fix-for-bulk-resources-generally-available)
 - [취약성에 대한 컨테이너 이미지 검사(미리 보기)](#scan-container-images-for-vulnerabilities-preview)
 - [추가 규정 준수 표준(미리 보기)](#additional-regulatory-compliance-standards-preview)
 - [Azure Kubernetes Service에 대한 위협 방지(미리 보기)](#threat-protection-for-azure-kubernetes-service-preview)
 - [가상 머신 취약성 평가(미리 보기)](#virtual-machine-vulnerability-assessment-preview)
 - [Azure Virtual Machines의 SQL Server에 대한 고급 데이터 보안(미리 보기)](#advanced-data-security-for-sql-servers-on-azure-virtual-machines-preview)
 - [사용자 지정 정책 지원(미리 보기)](#support-for-custom-policies-preview)
 - [커뮤니티 및 파트너를 위한 플랫폼으로 Azure Security Center 적용 범위 확장](#extending-azure-security-center-coverage-with-platform-for-community-and-partners)
 - [권장 사항 및 경고 내보내기와의 고급 통합(미리 보기)](#advanced-integrations-with-export-of-recommendations-and-alerts-preview)
 - [Windows 관리 센터에서 Security Center에 온-프레미스 서버 온보딩(미리 보기)](#onboard-on-prem-servers-to-security-center-from-windows-admin-center-preview)

### <a name="threat-protection-for-azure-key-vault-in-north-america-regions-preview"></a>북아메리카 지역에서 Azure Key Vault에 대 한 위협 방지 (미리 보기)

Azure Key Vault는 클라우드에서 키, 비밀, 암호화 키 및 정책을 중앙에서 관리하는 기능을 제공하여 데이터를 보호하고 클라우드 애플리케이션의 성능을 향상시키는 데 필수적인 서비스입니다. Azure Key Vault는 중요한 데이터와 중요 비즈니스용 데이터를 저장하므로 키 자격 증명 모음 및 여기에 저장된 데이터에 대한 보안을 최대화해야 합니다.

Azure Key Vault에 대한 위협 방지를 지원하는 Azure Security Center는 키 자격 증명 모음에 액세스하거나 악용하려는 비정상적인 잠재적 유해 시도를 탐지하는 추가 보안 인텔리전스 계층을 제공합니다. 이 새로운 보호 계층을 통해 고객은 보안 전문가가 되거나 보안 모니터링 시스템을 관리하지 않고도 키 자격 증명 모음에 대한 위협을 해결할 수 있습니다. 이 기능은 북아메리카 지역에서 공개 미리 보기로 제공됩니다.


### <a name="threat-protection-for-azure-storage-includes-malware-reputation-screening"></a>Azure Storage에 대한 위협 방지에 맬웨어 평판 차단 포함

Azure Storage에 대한 위협 방지는 해시 평판 분석 및 활성 Tor 종료 노드(프록시 익명화)로부터의 의심스러운 액세스를 사용하여 Azure Storage에 맬웨어 업로드를 탐지하기 위해 Microsoft Threat Intelligence에서 제공하는 새로운 탐지 기능을 제공합니다. 이제 Azure Security Center를 사용하여 스토리지 계정에서 검색된 맬웨어를 볼 수 있습니다.


### <a name="workflow-automation-with-logic-apps-preview"></a>Logic Apps로 워크플로 자동화(미리 보기)

중앙에서 관리되는 보안 및 IT/운영을 보유한 조직은 내부 워크플로 프로세스를 구현하여 환경에서 불일치가 발견될 때 조직 내에서 필요한 작업을 수행합니다. 대부분의 경우 이러한 워크플로는 반복 가능한 프로세스이며 자동화는 조직 내의 프로세스를 대폭 간소화할 수 있습니다.

고객이 Azure Logic Apps를 활용하는 자동화 구성을 만들고 권장 사항 또는 경고와 같은 특정 ASC 결과에 따라 자동으로 트리거하는 정책을 만들 수 있도록 하는 Security Center의 새로운 기능을 소개하겠습니다. Azure Logic App은 다양한 Logic App 커넥터 커뮤니티에서 지원하는 모든 사용자 지정 작업을 수행하거나, 이메일 보내기 또는 ServiceNow™ 티켓 열기와 같은 Security Center에서 제공하는 템플릿 중 하나를 사용하도록 구성할 수 있습니다.

워크플로를 실행하기 위한 자동 및 수동 Security Center 기능에 대한 자세한 내용은 [워크플로 자동화](workflow-automation.md)를 참조하세요.

Logic Apps를 만드는 방법에 대한 자세한 내용은 [Azure Logic Apps](../logic-apps/logic-apps-overview.md)를 참조하세요.


### <a name="quick-fix-for-bulk-resources-generally-available"></a>대량 리소스에 대한 빠른 수정 일반 공급

Secure Score의 일부로 사용자에게 제공되는 많은 작업으로 인해 대규모 문제를 효과적으로 해결하는 기능이 어려워질 수 있습니다.

보안 구성 오류 수정을 간소화하고 대량의 리소스에 대한 권장 사항을 빠르게 수정하고 보안 점수를 향상할 수 있도록 하려면 빠른 수정 재구성을 사용합니다.

이 작업을 통해 수정을 적용하려는 리소스를 선택하고 사용자 대신 설정을 구성하는 수정 작업을 시작할 수 있습니다.

빠른 수정은 현재 고객에게 Security Center 권장 사항 페이지의 일부로 일반 공급됩니다.

[보안 권장 사항에 대한 참조 가이드](recommendations-reference.md)에서 빠른 수정이 사용하도록 설정된 권장 사항을 확인하세요.


### <a name="scan-container-images-for-vulnerabilities-preview"></a>취약성에 대한 컨테이너 이미지 검사(미리 보기)

이제 Azure Security Center는 Azure Container Registry의 컨테이너 이미지의 취약성을 검사할 수 있습니다.

이미지 검사는 컨테이너 이미지 파일을 구문 분석한 다음 알려진 취약성이 있는지 확인하는 방식으로 작동합니다(Qualys 제공).

검사 자체는 Azure Container Registry에 새 컨테이너 이미지를 푸시할 때 자동으로 트리거됩니다. 발견된 취약성은 Security Center 권장 사항으로 나타나고 허용되는 공격 표면을 줄이기 위해 패치하는 방법에 대한 정보와 함께 Azure Secure Score에 포함됩니다.


### <a name="additional-regulatory-compliance-standards-preview"></a>추가 규정 준수 표준(미리 보기)

규정 준수 대시보드는 Security Center 평가를 기반으로 규정 준수 태세에 대한 인사이트를 제공합니다. 이 대시보드는 환경이 특정 규제 표준 및 업계 벤치마크에서 지정한 제어 및 요구 사항을 준수하는 방법을 보여 주고 이러한 요구 사항을 해결하는 방법에 대한 규범적인 권장 사항을 제공합니다.

규정 준수 대시보드는 다음 네 가지 기본 제공 표준을 지원했습니다.  Azure CIS 1.1.0, PCI-DSS, ISO 27001 및 SOC-TSP. 이제 다음과 같은 지원되는 추가 표준의 공개 미리 보기 릴리스를 발표합니다. NIST SP 800-53 4, SWIFT CSP CSCF v2020, 캐나다 연방 PBMM 및 영국 공식과 영국 NHS. 또한 표준에서 더 많은 제어를 제공하고 확장성을 개선하는 Azure CIS 1.1.0의 업데이트된 버전을 릴리스합니다.

[규정 준수 대시보드의 표준 집합을 사용자 지정하는 방법에 대해 자세히 알아봅니다](update-regulatory-compliance-packages.md).


### <a name="threat-protection-for-azure-kubernetes-service-preview"></a>Azure Kubernetes Service에 대한 위협 방지(미리 보기)

Kubernetes는 클라우드에서 소프트웨어를 배포하고 관리하기 위한 새로운 표준으로 빠르게 자리 잡고 있습니다. Kubernetes에 대한 풍부한 경험을 가지고 있는 사람은 거의 없으며 일반적으로 일반 엔지니어링 및 관리에만 중점을 두고 보안 측면을 간과하는 사람들이 많습니다. Kubernetes 환경을 안전하게 구성하여, 컨테이너에 초점을 맞춘 공격 표면 도어가 공격자에게 노출되지 않도록 해야 합니다. Security Center는 Azure에서 가장 빠르게 성장하는 서비스 중 하나인 AKS(Azure Kubernetes Service)로 컨테이너 공간의 지원을 확장하고 있습니다.

이 공개 미리 보기 릴리스의 새로운 기능은 다음과 같습니다.

- **검색 & 표시 유형** - Security Center의 등록된 구독 내에서 관리되는 AKS 인스턴스를 지속적으로 검색합니다.
- **Secure Score 권장 사항** - 고객의 Secure Score의 일부로 고객이 AKS의 보안 모범 사례를 준수하도록 돕는 실행 가능한 항목입니다(예: "역할 기반 액세스 제어를 사용하여 Kubernetes 서비스 클러스터에 대한 액세스를 제한해야 합니다.").
- **위협 탐지** - "권한 있는 컨테이너 탐지"와 같은 호스트 및 클러스터 기반 분석입니다.


### <a name="virtual-machine-vulnerability-assessment-preview"></a>가상 머신 취약성 평가(미리 보기)

가상 머신에 설치된 애플리케이션에는 가상 머신의 위험으로 이어질 수 있는 취약성이 있을 수 있습니다. Security Center 표준 계층에는 추가 비용 없이 가상 컴퓨터에 대 한 기본 제공 취약성 평가가 포함 되어 있습니다. 공개 미리 보기에서 Qualys가 제공하는 취약성 평가를 통해 가상 머신에 설치된 모든 애플리케이션을 지속적으로 검사하여 취약한 애플리케이션을 찾고 Security Center 포털의 환경에 대한 결과를 제공할 수 있습니다. Security Center는 모든 배포 작업을 처리하므로 사용자의 추가 작업이 필요하지 않습니다. 향후 고객의 고유한 비즈니스 요구 사항을 지원하기 위한 취약성 평가 옵션을 제공할 계획입니다.

[Azure Virtual Machines에 대한 취약성 평가에 대해 자세히 알아보세요](deploy-vulnerability-assessment-vm.md).


### <a name="advanced-data-security-for-sql-servers-on-azure-virtual-machines-preview"></a>Azure Virtual Machines의 SQL Server에 대한 고급 데이터 보안(미리 보기)

IaaS VM에서 실행되는 SQL DB에 대한 위협 방지 및 취약성 평가에 대한 Azure Security Center 지원은 현재 미리 보기로 제공됩니다.

[취약성 평가](../azure-sql/database/sql-vulnerability-assessment.md)는 잠재적인 데이터베이스 취약성을 검색, 추적 및 수정할 수 있는 서비스를 간편하게 구성합니다. Azure Secure Score의 일부로 보안 태세에 대한 가시성을 제공하고, 보안 문제를 해결하고 데이터베이스 보안을 강화하는 단계를 포함합니다.

[Advanced Threat Protection](../azure-sql/database/threat-detection-overview.md)은 비정상적이며 잠재적으로 유해할 수 있는 SQL Server 액세스 또는 악용 시도를 나타내는 비정상적인 활동을 검색합니다. 데이터베이스에서 의심스러운 활동을 지속적으로 모니터링하고 비정상적인 데이터베이스 액세스 패턴에 대해 작업 지향 보안 경고를 제공합니다. 이러한 경고는 의심스러운 활동 세부 정보와 위협을 조사하고 완화하기 위한 권장 조치를 제공합니다.


### <a name="support-for-custom-policies-preview"></a>사용자 지정 정책 지원(미리 보기)

Azure Security Center에서 이제 사용자 지정 정책을 지원합니다(미리 보기).

고객은 Azure Policy에서 만든 정책을 기반으로 자체 보안 평가를 사용하여 Security Center의 현재 보안 평가 범위를 확장했습니다. 사용자 지정 정책에 대한 지원을 통해 이제 이 기능을 사용할 수 있습니다.

이러한 새 정책은 Security Center 권장 사항 환경, Secure Score 및 규정 준수 표준 대시보드에 포함됩니다. 사용자 지정 정책 지원을 통해 이제 Azure Policy에서 사용자 지정 이니셔티브를 만든 다음 Security Center에서 정책으로 추가하고 권장 사항으로 시각화할 수 있습니다.


### <a name="extending-azure-security-center-coverage-with-platform-for-community-and-partners"></a>커뮤니티 및 파트너를 위한 플랫폼으로 Azure Security Center 적용 범위 확장

Security Center를 사용하면 Microsoft뿐만 아니라 Check Point, Tenable 및 CyberArk와 같은 파트너의 기존 솔루션에서 더 많은 통합이 제공되는 권장 사항을 받을 수 있습니다.  Security Center의 간단한 온보딩 흐름은 기존 솔루션을 Security Center에 연결하여 보안 태세 권장 사항을 한 곳에서 확인하고, 통합 보고서를 실행하며, 기본 제공 및 파트너 권장 사항에 대한 모든 Security Center 기능을 활용할 수 있습니다. Security Center 권장 사항을 파트너 제품으로 내보낼 수 있습니다.

[Microsoft 지능형 보안 연합에 대해 자세히 알아봅니다](https://www.microsoft.com/security/partnerships/intelligent-security-association).



### <a name="advanced-integrations-with-export-of-recommendations-and-alerts-preview"></a>권장 사항 및 경고 내보내기와의 고급 통합(미리 보기)

Security Center 맨 위에서 엔터프라이즈 수준 시나리오를 사용하도록 설정하기 위해 이제 Azure Portal 또는 API를 제외하고 추가 위치에서 Security Center 경고 및 권장 사항을 사용할 수 있습니다. 이를 이벤트 허브 및 Log Analytics 작업 영역으로 직접 내보낼 수 있습니다. 다음은 이러한 새 기능을 중심으로 만들 수 있는 몇 가지 워크플로입니다.

- Log Analytics 작업 영역으로 내보내기를 사용하면 Power BI를 사용하여 사용자 지정 대시보드를 만들 수 있습니다.
- 이벤트 허브로 내보내기를 사용하면 Security Center 경고 및 권장 사항을 타사 SIEM, 실시간으로 타사 솔루션 또는 Azure Data Explorer로 내보낼 수 있습니다.


### <a name="onboard-on-prem-servers-to-security-center-from-windows-admin-center-preview"></a>Windows 관리 센터에서 Security Center에 온-프레미스 서버 온보딩(미리 보기)

Windows Admin Center는 Azure에 배포되지 않은 Windows 서버용 관리 포털로, 백업 및 시스템 업데이트와 같은 몇 가지 Azure 관리 기능을 제공합니다. Windows 관리 센터 환경의 ASC에서 직접 보호하기 위해 이러한 비 Azure 서버를 온보딩하는 기능을 최근에 추가했습니다.

이 새로운 환경을 통해 사용자는 Azure Security Center에 WAC 서버를 온보딩하여 Windows 관리 센터 환경에서 직접 보안 경고 및 권장 사항을 볼 수 있습니다.


## <a name="september-2019"></a>2019년 9월

9월의 업데이트는 다음과 같습니다.

 - [적응형 애플리케이션 제어 향상으로 규칙 관리](#managing-rules-with-adaptive-application-controls-improvements)
 - [Azure Policy를 사용하여 컨테이너 보안 권장 사항 제어](#control-container-security-recommendation-using-azure-policy)

### <a name="managing-rules-with-adaptive-application-controls-improvements"></a>적응형 애플리케이션 제어 향상으로 규칙 관리

적응형 애플리케이션 제어를 사용하여 가상 머신에 대한 규칙을 관리하는 환경이 개선되었습니다. Azure Security Center의 적응형 애플리케이션 제어는 가상 머신에서 실행할 수 있는 애플리케이션을 제어하는 데 도움이 됩니다. 규칙 관리의 일반적인 향상 외에도 새 혜택을 통해 새 규칙을 추가할 때 보호할 파일 형식을 제어할 수 있습니다.

[적응형 애플리케이션 제어에 대해 자세히 알아봅니다](security-center-adaptive-application.md).


### <a name="control-container-security-recommendation-using-azure-policy"></a>Azure Policy를 사용하여 컨테이너 보안 권장 사항 제어

컨테이너 보안의 취약성을 해결하는 Azure Security Center 권장 사항은 이제 Azure Policy를 통해 사용하거나 사용하지 않도록 설정할 수 있습니다.

사용하도록 설정된 보안 정책을 보려면 Security Center에서 보안 정책 페이지를 엽니다.


## <a name="august-2019"></a>2019년 8월

8월의 업데이트는 다음과 같습니다.

 - [Azure Firewall에 대한 JIT(just-in-time) VM 액세스](#just-in-time-jit-vm-access-for-azure-firewall)
 - [보안 태세를 높이기 위한 단일 클릭 수정(미리 보기)](#single-click-remediation-to-boost-your-security-posture-preview)
 - [테넌트 간 관리](#cross-tenant-management)

### <a name="just-in-time-jit-vm-access-for-azure-firewall"></a>Azure Firewall에 대한 JIT(just-in-time) VM 액세스 

이제 Azure Firewall에 대한 JIT(just-in-time) VM 액세스가 일반 공급됩니다. 이를 사용하여 NSG 보호 환경 외에도 Azure Firewall 보호 환경을 보호합니다.

JIT VM 액세스는 NSG 및 Azure Firewall 규칙을 사용하여 필요한 경우에만 VM에 제어된 액세스를 제공하여 네트워크 대규모 공격에 대한 노출을 줄입니다.

VM에 JIT를 사용하도록 설정하는 경우 보호될 포트, 포트가 열려 있는 상태로 유지되는 기간 및 이러한 포트에 액세스하도록 승인된 IP 주소를 결정하는 정책을 만듭니다. 이 정책은 사용자가 액세스를 요청할 때 수행할 수 있는 작업을 제어하는 데 도움이 됩니다.

요청은 Azure 활동 로그에 기록되므로 액세스를 쉽게 모니터링하고 감사할 수 있습니다. JIT(just-in-time) 페이지를 사용하면 JIT가 사용하도록 설정된 기존 VM과 JIT가 권장되는 VM을 빠르게 식별할 수 있습니다.

[Azure Firewall에 대해 자세히 알아보세요](../firewall/overview.md).


### <a name="single-click-remediation-to-boost-your-security-posture-preview"></a>보안 태세를 높이기 위한 단일 클릭 수정(미리 보기)

보안 점수는 워크로드 보안에 대한 사용자의 대비 상태를 평가할 수 있는 도구입니다. 이는 사용자의 보안 권장 사항을 검토하고 순위를 지정하므로 사용자는 먼저 수행할 권장 사항을 파악할 수 있습니다. 이를 통해 가장 심각한 보안 취약성을 찾아내 조사의 순위를 지정할 수 있습니다.

보안 구성 오류 수정을 간소화하고 보안 점수를 빠르게 개선할 수 있도록 한 번의 클릭으로 대량의 리소스에 대한 권장 사항을 수정할 수 있는 새로운 기능이 추가되었습니다.

이 작업을 통해 수정을 적용하려는 리소스를 선택하고 사용자 대신 설정을 구성하는 수정 작업을 시작할 수 있습니다.

[보안 권장 사항에 대한 참조 가이드](recommendations-reference.md)에서 빠른 수정이 사용하도록 설정된 권장 사항을 확인하세요.


### <a name="cross-tenant-management"></a>테넌트 간 관리

Security Center는 이제 Azure Lighthouse의 일부로 교차 테넌트 관리 시나리오를 지원합니다. 이를 통해 Security Center에서 여러 테넌트의 보안 태세를 파악하고 관리할 수 있습니다. 

[테넌트 간 관리 환경에 대해 자세히 알아보세요](security-center-cross-tenant-management.md).


## <a name="july-2019"></a>2019년 7월

### <a name="updates-to-network-recommendations"></a>네트워크 권장 사항 업데이트

ASC(Azure Security Center)에서 새로운 네트워킹 권장 사항을 출시하고 기존 권장 사항을 개선했습니다. 이제 Security Center를 사용하면 리소스에 대해 훨씬 더 강력한 네트워킹 보호를 보장합니다. 

[네트워크 권장 사항에 대해 자세히 알아봅니다](recommendations-reference.md#recs-network).


## <a name="june-2019"></a>2019년 6월

### <a name="adaptive-network-hardening---generally-available"></a>적응형 네트워크 강화 - 일반 공급

공용 클라우드에서 실행되는 워크로드에 대한 가장 큰 공격 노출 영역 중 하나는 공용 인터넷과의 연결입니다. 고객은 Azure 워크로드를 필요한 원본 범위에만 사용할 수 있도록 하기 위해 어떤 NSG(네트워크 보안 그룹) 규칙을 사용해야 하는지 파악하기 어렵습니다. 이 기능을 통해 Security Center는 Azure 워크로드의 네트워크 트래픽 및 연결 패턴을 학습하고 인터넷 연결 가상 머신에 대한 NSG 규칙 권장 사항을 제공합니다. 이를 통해 고객은 네트워크 액세스 정책을 더 잘 구성하고 공격에 대한 노출을 제한할 수 있습니다. 

[적응형 네트워크 강화에 대해 자세히 알아봅니다.](security-center-adaptive-network-hardening.md)