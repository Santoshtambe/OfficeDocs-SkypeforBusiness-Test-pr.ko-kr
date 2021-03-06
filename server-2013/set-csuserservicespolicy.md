﻿---
title: Set-CsUserServicesPolicy
TOCTitle: Set-CsUserServicesPolicy
ms:assetid: fbe18ddf-5094-4d8b-ad27-75b73173b8c4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205414(v=OCS.15)
ms:contentKeyID: 49305632
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsUserServicesPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 사용자 서비스 정책을 수정합니다. 사용자 서비스 정책은 사용자의 연락처가 Lync Server 2013에 저장되는지 아니면 통합 연락처 저장소에 저장되는지를 결정합니다. 사용자는 통합 연락처 저장소를 통해 Lync 2013, Outlook 및/또는 Outlook Web Access를 사용하여 액세스할 수 있는 단일 연락처 집합을 유지 관리할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Set-CsUserServicesPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsUserServicesPolicy [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-UcsAllowed <$true | $false>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 사용자별 사용자 서비스 정책 RedmondUserServicesPolicy를 사용하지 않도록 설정합니다. 즉, 이 정책을 통해 관리되는 사용자의 연락처가 통합 연락처 저장소에 저장되지 않습니다.

    Set-CsUserServicesPolicy -Identity "RedmondUserServicesPolicy" -UcsAllowed $False

## 예제 2

예제 2에서는 사이트 범위에서 구성된 모든 사용자 서비스 정책을 수정하여 통합 연락처 저장소를 사용하지 않도록 설정합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsUserServicesPolicy** cmdlet 및 Filter 매개 변수를 호출하여 사이트 범위에서 구성된 모든 정책의 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 각 정책을 가져와 UcsAllowed 속성을 False($False)로 설정하는 **Set-CsUserServicesPolicy** cmdlet에 파이프됩니다.

    Get-CsUserServicesPolicy -Filter "site:*" | Set-CsUserServicesPolicy -UcsAllowed $False

## 자세한 정보

Lync Server 2013에서 도입된 통합 연락처 저장소를 통해 관리자는 Lync Server가 아닌 Microsoft Exchange Server 2013에서 사용자 연락처를 저장할 수 있습니다. 그러면 사용자가 Lync 2013에서는 물론 Outlook과 Outlook Web Access에서도 같은 연락처 집합에 액세스할 수 있습니다. 계속 Lync Server 2013에서 연락처를 저장할 수도 있는데, 이 경우 사용자는 서로 다른 두 연락처 집합(Outlook 및 Outlook Web Access에서 사용할 연락처 집합과 Lync 2013에서 사용할 연락처 집합)을 유지 관리해야 합니다.

통합 연락처 저장소를 활용하려면 우선 통합 연락처 저장소를 사용할 수 있도록 설정하는 사용자 서비스 정책을 사용자에게 할당해야 합니다. 전역, 사이트 또는 사용자별 범위에서 구성할 수 있는 사용자 서비스 정책은 하나의 속성, 즉 UcsAllowed만 포함합니다. 이 속성을 True로 설정하는 경우 기타 모든 전제 조건이 충족되었다고 가정할 때 다음 번에 사용자가 Lync Server 2013에 로그온하면 사용자의 연락처가 통합 연락처 저장소로 자동 마이그레이션됩니다.

이 속성을 False로 설정하면 이와 같은 자동 마이그레이션이 수행되지 않습니다. 그러나 UcsAllowed만 설정한다고 해서 사용자 연락처가 통합 연락처 저장소에서 Lync Server로 다시 이동되지는 않습니다. 이러한 이동을 수행하려면 먼저 통합 연락처 저장소 사용을 허용하지 않는 사용자 서비스 정책을 사용자에게 할당해야 합니다. 그 후에는 **Invoke-CsUcsRollback** cmdlet을 사용하여 연락처를 통합 연락처 저장소에서 Lync Server로 다시 "수동으로" 마이그레이션해야 합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsUserServicesPolicy"}

**Lync Server 제어판:** **Set-CsUserServicesPolicy** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

## 매개 변수


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>매개 변수</th>
<th>필수</th>
<th>유형</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다. 명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 정책의 고유 식별자입니다. 전역 정책을 수정하려면 다음 구문을 사용합니다.</p>
<p>-Identity &quot;global&quot;</p>
<p>사이트 범위에서 구성된 정책을 수정하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;site:Redmond&quot;</p>
<p>서비스 범위에서 구성된 정책을 수정하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;UserServer:atl-cs-001.litwareinc.com&quot;</p>
<p>사용자 서비스 정책을 호스트할 수 있는 서비스는 UserServer 서비스뿐입니다.</p>
<p>이 매개 변수를 포함하지 않으면 <strong>Set-CsUserServicesPolicy</strong> cmdlet이 자동으로 전역 정책을 수정합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSObject</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>해당 사용자 서비스 정책을 수정할 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally Unique Identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>-Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
</tr>
<tr class="even">
<td><p><em>UcsAllowed</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>기본값인 True로 설정하면 정책이 적용되는 사용자가 통합 연락처 저장소로 자동 마이그레이션됩니다(사용자가 Microsoft Exchange Server 2013에서 계정을 소유하고 있으며 Lync 2013을 사용하여 로그온한다고 가정함). False로 설정하면 사용자를 통합 연락처 저장소에서 제거할 수 있지만 이 경우 <strong>Invoke-CsUcsRollback</strong> cmdlet을 통해 사용자를 &quot;수동으로&quot; 제거해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

**Set-CsUserServicesPolicy** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.UserServices.UserServicesPolicy 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Set-CsUserServicesPolicy** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.UserServices.UserServicesPolicy 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsUserServicesPolicy](get-csuserservicespolicy.md)  
[Grant-CsUserServicesPolicy](grant-csuserservicespolicy.md)  
[New-CsUserServicesPolicy](new-csuserservicespolicy.md)  
[Remove-CsUserServicesPolicy](remove-csuserservicespolicy.md)

