---
title: Azure Data Factory를 시각적으로 모니터링
description: Azure Data Factory를 시각적으로 모니터링하는 방법에 대해 알아봅니다
services: data-factory
documentationcenter: ''
author: djpmsft
ms.author: daperlov
ms.reviewer: maghan
ms.service: data-factory
ms.workload: data-services
ms.topic: conceptual
ms.date: 06/30/2020
ms.openlocfilehash: ecb066c7269217af3f8cc84e0f59ab29b4b39a9e
ms.sourcegitcommit: 46c5ffd69fa7bc71102737d1fab4338ca782b6f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2020
ms.locfileid: "94331515"
---
# <a name="visually-monitor-azure-data-factory"></a>Azure Data Factory를 시각적으로 모니터링

[!INCLUDE[appliesto-adf-xxx-md](includes/appliesto-adf-xxx-md.md)]

Azure Data Factory에서 파이프라인을 만들어 게시한 후에는 트리거와 연결하거나 임시 실행을 수동으로 시작할 수 있습니다. Azure Data Factory 사용자 환경에서 기본적으로 모든 파이프라인 실행을 모니터링할 수 있습니다. 모니터링 환경을 열려면 [Azure Portal](https://portal.azure.com/)의 data factory 블레이드에서 **모니터 & 관리** 타일을 선택합니다. ADF UX에 이미 있는 경우 왼쪽 사이드바에서 **모니터** 아이콘을 클릭합니다.

기본적으로 모든 데이터 팩터리 실행은 브라우저의 현지 표준 시간대로 표시 됩니다. 표준 시간대를 변경하는 경우 모든 날짜/시간 필드가 선택한 항목에 맞춰집니다.

## <a name="monitor-pipeline-runs"></a>파이프라인 실행 모니터링

기본 모니터링 보기는 선택한 기간에 트리거된 파이프라인 실행의 목록입니다. 시간 범위를 변경 하 고 상태, 파이프라인 이름 또는 주석을 기준으로 필터링 할 수 있습니다. 특정 파이프라인 실행을 마우스로 가리켜 다시 실행 및 소비 보고서와 같은 실행 관련 작업을 가져옵니다.

![파이프라인 실행 모니터링용 목록 보기](media/monitor-visually/pipeline-runs.png)

파이프라인 실행 표에는 다음 열이 포함 되어 있습니다.

| **열 이름** | **설명** |
| --- | --- |
| 파이프라인 이름 | 파이프라인 이름입니다. |
| 실행 시작 | 파이프라인 실행에 대한 시작 날짜 및 시간(MM/DD/YYYY, HH: MM: SS AM/PM) |
| 실행 종료 | 파이프라인 실행의 종료 날짜 및 시간 (MM/DD/YYYY, HH: MM: SS AM/PM) |
| Duration | 실행 기간 (HH:MM:SS) |
| 트리거 주체 | 파이프라인을 시작한 트리거의 이름입니다. |
| 상태 | **실패** , **성공** , **진행 중** , **취소** 또는 **큐 대기** |
| 주석 | 파이프라인에 연결된 필터링 가능한 태그  |
| 매개 변수 | 파이프라인 실행 매개 변수 (이름/값 쌍) |
| Error | 파이프라인이 실패한 경우 실행 오류 |
| 실행 ID | 파이프라인 실행 ID입니다. |

파이프라인 및 활동 실행 목록을 새로 고치려면 **새로 고침** 단추를 수동으로 선택해야 합니다. 자동 새로 고침은 현재 지원되지 않습니다.

![새로 고침 단추](media/monitor-visually/refresh.png)

디버그 실행의 결과를 보려면 **디버그** 탭을 선택 합니다.

![활성 디버그 실행 보기 아이콘 선택](media/iterative-development-debugging/view-debug-runs.png)

## <a name="monitor-activity-runs"></a>작업 실행 모니터링

특정 파이프라인 실행의 개별 작업 실행에 대 한 자세한 보기를 가져오려면 파이프라인 이름을 클릭 합니다.

![활동 실행 보기](media/monitor-visually/view-activity-runs.png)

목록 보기에는 각 파이프라인 실행에 해당하는 작업 실행이 표시됩니다. 특정 작업 실행을 마우스로 가리켜 JSON 입력, JSON 출력 및 자세한 작업 관련 모니터링 환경과 같은 실행 관련 정보를 가져옵니다.

![작업 실행 모니터링 목록 보기](media/monitor-visually/activity-runs.png)

| **열 이름** | **설명** |
| --- | --- |
| 작업 이름 | 파이프라인 내 작업 이름 |
| 작업 유형 | **복사** , **ExecuteDataFlow** 또는 **AzureMLExecutePipeline** 같은 작업 유형 |
| 동작 | JSON 입력 정보, JSON 출력 정보 또는 자세한 작업 관련 모니터링 환경을 볼 수 있는 아이콘 | 
| 실행 시작 | 작업 실행에 대한 시작 날짜 및 시간(MM/DD/YYYY, HH: MM: SS AM/PM) |
| Duration | 실행 기간 (HH:MM:SS) |
| 상태 | **실패** , **성공** , **진행 중** 또는 **취소** |
| 통합 런타임 | 작업이 실행된 Integration Runtime |
| 사용자 속성 | 작업의 사용자 정의 속성 |
| Error | 작업이 실패한 경우 실행 오류 |
| 실행 ID | 활동 실행 ID입니다. |

작업에 실패 한 경우 오류 열의 아이콘을 클릭 하 여 자세한 오류 메시지를 볼 수 있습니다. 

![작업 실행 모니터링 목록 보기](media/monitor-visually/activity-run-error.png)

### <a name="promote-user-properties-to-monitor"></a>모니터링하도록 사용자 속성 승격

모니터링하는 엔터티가 되도록 파이프라인 작업 속성을 사용자 속성으로 승격합니다. 예를 들어 파이프라인에서 복사 작업의 **원본** 및 **대상** 속성을 사용자 속성으로 승격할 수 있습니다.

> [!NOTE]
> 최대 5개의 파이프라인 작업 속성만을 사용자 속성으로 승격할 수 있습니다.

![사용자 속성 만들기](media/monitor-visually/promote-user-properties.png)

사용자 속성을 만든 후에 모니터링 목록 보기에서 모니터링할 수 있습니다.

![활동 실행 목록에 사용자 속성에 대한 열 추가](media/monitor-visually/choose-user-properties.png)

 복사 작업의 원본이 테이블 이름인 경우 원본 테이블 이름을 활동 실행 목록 보기의 열로 모니터링할 수 있습니다.

![사용자 속성의 열을 포함한 활동 실행 목록](media/monitor-visually/view-user-properties.png)

## <a name="rerun-pipelines-and-activities"></a>파이프라인 및 작업 다시 실행

이전에 시작에서 실행 한 파이프라인을 다시 실행 하려면 특정 파이프라인 실행을 마우스로 가리키고 **다시 실행** 을 선택 합니다. 여러 파이프라인을 선택 하는 경우 **다시** 실행 단추를 사용 하 여 모든 파이프라인을 실행할 수 있습니다.

![파이프라인 다시 실행](media/monitor-visually/rerun-pipeline.png)

특정 지점에서 시작 하는 작업을 다시 실행 하려는 경우에는 작업 실행 보기에서 작업을 수행할 수 있습니다. 시작 하려는 작업을 선택 하 고 **작업에서 다시 실행** 을 선택 합니다. 

![작업 실행 다시 실행](media/monitor-visually/rerun-activity.png)

### <a name="rerun-from-failed-activity"></a>실패한 활동에서 다시 실행

작업이 실패하나, 시간이 초과하거나, 취소되는 경우 **실패한 작업에서 다시 실행** 을 선택하여 실패한 작업에서 파이프라인을 다시 실행할 수 있습니다.

![실패한 작업 다시 실행](media/monitor-visually/rerun-failed-activity.png)

### <a name="view-rerun-history"></a>다시 실행 기록 보기

목록 보기에서 모든 파이프라인 실행의 다시 실행 기록을 볼 수 있습니다.

![기록 보기](media/monitor-visually/rerun-history-1.png)

특정 파이프라인 실행의 다시 실행 기록을 볼 수도 있습니다.

![파이프라인 실행의 기록 보기](media/monitor-visually/view-rerun-history.png)

## <a name="monitor-consumption"></a>사용량 모니터링

실행 옆에 있는 사용량 아이콘을 클릭하여 파이프라인 실행에서 사용된 리소스를 볼 수 있습니다. 

![파이프라인에서 사용 하는 리소스를 볼 수 있는 위치를 보여 주는 스크린샷](media/monitor-visually/monitor-consumption-1.png)

아이콘을 클릭하면 해당 파이프라인 실행에 사용되는 리소스의 사용량 보고서가 열립니다. 

![사용량 모니터링](media/monitor-visually/monitor-consumption-2.png)

이러한 값을 [Azure 가격 계산기](https://azure.microsoft.com/pricing/details/data-factory/)에 연결하여 파이프라인 실행 비용을 예측할 수 있습니다. Azure Data Factory 가격 책정에 대한 자세한 내용은 [가격 책정 이해](pricing-concepts.md)를 참조하세요.

> [!NOTE]
> 가격 계산기에서 반환되는 값은 예상치입니다. Azure Data Factory가 청구하는 정확한 금액을 반영하지는 않습니다. 

## <a name="gantt-views"></a>Gantt 보기

Gantt 차트는 시간 범위에 대 한 실행 기록을 볼 수 있는 뷰입니다. Gantt 보기로 전환 하면 모든 파이프라인 실행을 이름별로 그룹화 하 여 실행이 걸린 시간을 기준으로 막대로 표시 하는 것을 볼 수 있습니다. 파이프라인에서 만든 주석/태그를 기준으로 그룹화 할 수도 있습니다. 활동 실행 수준 에서도 Gantt 보기를 사용할 수 있습니다.

![Gantt 차트의 예](media/monitor-visually/select-gantt.png)

막대의 길이는 파이프라인의 기간을 알려줍니다. 막대를 선택하여 자세한 내용을 볼 수도 있습니다.

![Gantt 차트 기간](media/monitor-visually/view-gantt-run.png)

## <a name="alerts"></a>경고

Data Factory의 지원되는 메트릭에 대해 경고를 발생시킬 수 있습니다. 시작하려면 Data Factory 모니터링 페이지에서 **모니터링** > **경고 및 메트릭** 을 선택합니다.

![데이터 팩터리 모니터링 페이지](media/monitor-visually/start-page.png)

7분 동안 이 기능의 소개 및 데모에 대한 다음 비디오를 시청하세요.

> [!VIDEO https://channel9.msdn.com/shows/azure-friday/Monitor-your-Azure-Data-Factory-pipelines-proactively-with-alerts/player]

### <a name="create-alerts"></a>경고 만들기

1.  **새로운 경고 규칙** 을 선택하여 새 경고를 만듭니다.

    ![새 경고 규칙 단추](media/monitor-visually/new-alerts.png)

1.  규칙 이름을 지정하고 경고 심각도를 선택합니다.

    ![규칙 이름 및 심각도 상자](media/monitor-visually/name-and-severity.png)

1.  경고 조건을 선택합니다.

    ![대상 조건을 위한 상자](media/monitor-visually/add-criteria-1.png)

    ![경고 조건을 설정 하기 위해 하나의 메트릭을 선택 하는 위치를 보여 주는 스크린샷](media/monitor-visually/add-criteria-2.png)

    ![조건 목록](media/monitor-visually/add-criteria-3.png)

    SSIS 패키지 실행 및 SSIS IR 시작/중지 작업 뿐만 아니라 ADF 엔터티 수/크기, 작업/파이프라인/트리거 실행, IR (Integration Runtime) CPU 사용률/메모리/노드 수/큐에 대 한 경고를 비롯 하 여 다양 한 메트릭에 대 한 경고를 만들 수 있습니다.

1.  경고 논리를 구성합니다. 모든 파이프라인 및 해당 활동의 선택한 메트릭에 대해 경고를 만들 수 있습니다. 특정 활동 유형, 활동 이름, 파이프라인 이름 또는 오류 유형을 선택할 수도 있습니다.

    ![경고 논리를 구성하기 위한 옵션](media/monitor-visually/alert-logic.png)

1.  경고에 대해 이메일, SMS, 푸시, 음성 알림을 구성합니다. 경고 알림에 대해 작업 그룹을 만들거나 기존 작업 그룹을 선택합니다.

    ![경고 알림 구성 옵션](media/monitor-visually/configure-notification-1.png)

    ![알림 추가 옵션](media/monitor-visually/configure-notification-2.png)

1.  경고 규칙을 만듭니다.

    ![경고 규칙을 만드는 옵션](media/monitor-visually/create-alert-rule.png)

## <a name="next-steps"></a>다음 단계

파이프라인 모니터링 및 관리에 대한 자세한 내용은 [프로그래밍 방식으로 파이프라인 모니터링 및 관리](./monitor-programmatically.md) 문서를 참조하세요.