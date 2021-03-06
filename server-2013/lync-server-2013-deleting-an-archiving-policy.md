﻿---
title: 보관 정책 삭제
TOCTitle: 보관 정책 삭제
ms:assetid: 4739a691-41cc-4128-8bb8-6d5a4c02107a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg520989(v=OCS.15)
ms:contentKeyID: 49303513
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 보관 정책 삭제

 

_**마지막으로 수정된 항목:** 2013-02-23_

사용자 정책 또는 사이트 정책을 삭제할 수 있습니다. 전역 정책은 제거할 수 없습니다. 전역 정책을 제거하려고 시도하면 Lync Server 2013이 정책을 기본값으로 자동으로 다시 설정합니다.


> [!NOTE]
> 배포에서 Microsoft Exchange 통합을 사용하도록 설정한 경우 Exchange 정책은 Exchange 2013에 있고 해당 사서함이 원본 위치 유지로 설정된 사용자에 대해 보관을 설정할지 여부를 제어합니다. 자세한 내용은 배포 설명서에서 <A href="lync-server-2013-setting-up-policies-for-archiving-when-using-exchange-server-integration.md">Exchange Server 통합 사용 시 보관용 정책 설정</A>을 참조하십시오.



## 보관을 위해 사용자 또는 사이트 정책을 삭제하려면

1.  CsArchivingAdministrator 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **모니터링 및 보관**을 클릭하고 **보관 정책**을 클릭합니다.

4.  보관 정책 목록에서 삭제하려는 사용자 또는 사이트 정책을 클릭하고, **편집**을 클릭한 후 **삭제**를 클릭합니다.

5.  **커밋**을 클릭합니다.

## Lync Server 관리 셸 Cmdlet을 사용하여 보관 정책 제거

보관 정책은 Windows PowerShell 및 **Remove-CsArchivingPolicy** cmdlet을 사용하여 삭제할 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요..

## 지정된 보관 정책 제거

  - 한 예로, **Remove-CsArchivingPolicy**는 Identity가 site:Redmond인 정책을 삭제합니다. 사이트 범위로 구성된 정책을 삭제하면 해당 사이트 정책으로 이전에 관리되던 사용자가 자동으로 이전 정책 대신 전역 보관 정책에 의해 제어됩니다. 다음 명령은 Redmond 사이트에 적용된 보관 기능을 제거합니다.
    
        Remove-CsArchivingPolicy -Identity site:Redmond

## 사용자별 범위에 적용된 모든 보관 정책 제거

  - 이 명령은 사용자별 범위에 적용된 모든 보관 정책을 제거합니다.
    
        Get-CsArchivingPolicy -Filter "tag:*" | Remove-CsArchivingPolicy

## 내부 보관을 사용하지 않도록 설정하는 모든 보관 정책 제거

  - 이 명령은 내부 보관이 해제된 모든 보관 정책을 제거합니다.
    
        Get-CsArchivingPolicy | Where-Object {$_.ArchiveInternal -eq $False} | Remove-CsArchivingPolicy

자세한 내용은 [Remove-CsArchivingPolicy](remove-csarchivingpolicy.md) cmdlet의 도움말 항목을 참조하십시오.

## 참고 항목

#### 기타 리소스

[Lync Server 2013에서 내부 및 외부 통신의 보관 관리](lync-server-2013-managing-the-archiving-of-internal-and-external-communications.md)

