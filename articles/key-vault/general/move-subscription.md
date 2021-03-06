---
title: 자격 증명 모음을 다른 구독으로 이동하는 Azure Key Vault | Microsoft Docs
description: 키 자격 증명 모음을 다른 구독으로 이동 하는 방법에 대한 지침입니다.
services: key-vault
author: ShaneBala-keyvault
manager: ravijan
tags: azure-resource-manager
ms.service: key-vault
ms.subservice: general
ms.topic: how-to
ms.date: 05/05/2020
ms.author: sudbalas
Customer intent: As a key vault administrator, I want to move my vault to another subscription.
ms.openlocfilehash: e0cd4cad74257dbf83ec8d30405eacca341a8d31
ms.sourcegitcommit: 7863fcea618b0342b7c91ae345aa099114205b03
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93289529"
---
# <a name="moving-an-azure-key-vault-to-another-subscription"></a>다른 구독으로 Azure Key Vault 이동

[!INCLUDE [updated-for-az](../../../includes/updated-for-az.md)]

## <a name="overview"></a>개요

> [!IMPORTANT]
> **키 자격 증명 모음을 다른 구독으로 이동하면 환경에 대한 주요 변경 내용이 발생합니다.**
> 키 자격 증명 모음을 새 구독으로 이동하도록 결정하기 전에 이러한 변경의 영향을 이해하고 이 문서의 지침을 따라야 합니다.
> MSI (관리 서비스 Id)를 사용 하는 경우 문서 끝에 있는 이동 후 지침을 읽어 보세요. 

키 자격 증명 모음을 만들 때 생성된 해당 구독에 대한 기본 Azure Active Directory 테넌트 ID에 자동으로 연결됩니다. 모든 액세스 정책 항목은 이 테넌트 ID에 연결됩니다. Azure 구독을 테넌트 A에서 테넌트 B로 이동하는 경우 기존 키 자격 증명 모음에는 테넌트 B의 서비스 주체(사용자 및 애플리케이션)가 액세스할 수 없게 됩니다. 이 문제를 해결하려면 다음을 수행해야 합니다.

* 이 구독에 있는 모든 기존 Key Vaults와 연결된 테넌트 ID를 테넌트 B로 변경합니다.
* 모든 기존 액세스 정책 항목을 제거합니다.
* 테넌트 B와 연결된 새 액세스 정책 항목을 추가합니다.

## <a name="limitations"></a>제한 사항

> [!IMPORTANT]
> **디스크 암호화에 사용 되는 키 자격 증명 모음은 이동할 수 없습니다** . VM에 대 한 디스크 암호화를 사용 하는 key vault를 사용 하는 경우 디스크 암호화를 사용 하는 동안에는 key vault를 다른 리소스 그룹 또는 구독으로 이동할 수 없습니다. 키 자격 증명 모음을 새 리소스 그룹 또는 구독으로 이동 하기 전에 디스크 암호화를 사용 하지 않도록 설정 해야 합니다. 

일부 서비스 주체(사용자 및 애플리케이션)는 특정 테넌트에 바인딩됩니다. 키 자격 증명 모음을 다른 테넌트의 구독으로 이동하면 특정 서비스 주체에 대한 액세스를 복원할 수 없게 됩니다. 키 자격 증명 모음을 이동하는 테넌트에 모든 필수 서비스 주체가 존재하는지 확인합니다.

## <a name="design-considerations"></a>디자인 고려 사항

조직에서 구독 수준에서 적용 또는 제외를 사용하여 Azure Policy를 구현했을 수도 있습니다. 키 자격 증명 모음이 현재 존재하는 구독과 키 자격 증명을 이동하려는 구독의 정책 할당 세트가 서로 다를 수 있습니다. 정책 요구 사항의 충돌로 인해 애플리케이션이 중단될 수 있습니다.

### <a name="example"></a>예제

2년 동안 유효한 인증서를 생성하는 키 자격 증명 모음에 연결된 애플리케이션이 있습니다. 키 자격 증명 모음을 이동하려는 구독에는 1년 이상 유효한 인증서 생성을 차단하는 정책 할당이 있습니다. 키 자격 증명 모음을 새 구독으로 이동한 후 2년 동안 유효한 인증서를 만드는 작업은 Azure 정책 할당에 의해 차단됩니다.

### <a name="solution"></a>해결 방법

Azure Portal에서 Azure Policy 페이지로 이동하고 현재 구독에 대한 정책 할당과 이동 중인 구독을 확인하고 불일치 항목이 없는지 확인합니다.

## <a name="prerequisites"></a>사전 요구 사항

* 키 자격 증명 모음이 있는 현재 구독에 대한 기여자 수준 액세스 이상.
* 키 자격 증명 모음을 이동하려는 구독에 대한 기여자 수준 액세스 이상.
* 새 구독의 리소스 그룹.

## <a name="procedure"></a>절차

### <a name="moving-key-vault-to-a-new-subscription-within-the-same-tenant"></a>동일한 테 넌 트 내의 새 구독으로 Key Vault 이동

1. Azure Portal에 로그인
2. 키 자격 증명 모음으로 이동
3. “개요” 탭을 클릭
4. “이동” 단추를 선택
5. 드롭다운 옵션에서 “다른 구독으로 이동” 선택
6. 키 자격 증명 모음을 이동할 리소스 그룹을 선택
7. 리소스 이동과 관련된 경고 승인
8. "확인" 선택

### <a name="additional-steps-if-you-moved-key-vault-to-a-subscription-in-a-new-tenant"></a>주요 자격 증명 모음을 새 테 넌 트의 구독으로 이동한 경우 추가 단계

키 자격 증명 모음을 새 테 넌 트의 구독으로 이동한 경우 수동으로 테 넌 트 ID를 업데이트 하 고 이전 액세스 정책을 제거 해야 합니다. PowerShell 및 Azure CLI의 이러한 단계에 대한 자습서는 다음과 같습니다. PowerShell을 사용 하는 경우 현재 선택 된 범위 외부의 리소스를 볼 수 있도록 아래에 설명 된 Clear-AzContext 명령을 실행 해야 할 수 있습니다. 

```azurepowershell
Select-AzSubscription -SubscriptionId <your-subscriptionId>                # Select your Azure Subscription
$vaultResourceId = (Get-AzKeyVault -VaultName myvault).ResourceId          # Get your key vault's Resource ID 
$vault = Get-AzResource -ResourceId $vaultResourceId -ExpandProperties     # Get the properties for your key vault
$vault.Properties.TenantId = (Get-AzContext).Tenant.TenantId               # Change the Tenant that your key vault resides in
$vault.Properties.AccessPolicies = @()                                     # Access policies can be updated with real
                                                                           # applications/users/rights so that it does not need to be                             # done after this whole activity. Here we are not setting 
                                                                           # any access policies. 
Set-AzResource -ResourceId $vaultResourceId -Properties $vault.Properties  # Modifies the key vault's properties.

Clear-AzContext                                                            #Clear the context from PowerShell
Connect-AzAccount                                                          #Log in again to confirm you have the correct tenant id
````

```azurecli
az account set -s <your-subscriptionId>                                    # Select your Azure Subscription
tenantId=$(az account show --query tenantId)                               # Get your tenantId
az keyvault update -n myvault --remove Properties.accessPolicies           # Remove the access policies
az keyvault update -n myvault --set Properties.tenantId=$tenantId          # Update the key vault tenantId
```

이제 자격 증명 모음이 올바른 테넌트 ID와 연결되고 이전 액세스 정책 항목이 제거되었으므로 Azure PowerShell [Set-AzKeyVaultAccessPolicy](/powershell/module/az.keyvault/Set-azKeyVaultAccessPolicy) cmdlet 또는 Azure CLI [az keyvault set-policy](/cli/azure/keyvault?view=azure-cli-latest#az-keyvault-set-policy) 명령을 사용하여 새 액세스 정책 항목을 설정합니다.

Azure 리소스에 관리 되는 id를 사용 하는 경우 새 Azure Active Directory 테 넌 트로도 업데이트 해야 합니다. 관리 id에 대 한 자세한 내용은 [관리 id 개요](../../active-directory/managed-identities-azure-resources/overview.md)를 확인 하세요.

관리 id를 사용 하는 경우 이전 id가 더 이상 올바른 Azure Active Directory 테 넌 트에 없으므로 id도 업데이트 해야 합니다. 이 문제를 해결 하려면 다음 문서를 참조 하세요. 

* [MSI 업데이트](../../active-directory/managed-identities-azure-resources/known-issues.md#transferring-a-subscription-between-azure-ad-directories)
* [새 디렉터리로 구독 전송](../../role-based-access-control/transfer-subscription.md)