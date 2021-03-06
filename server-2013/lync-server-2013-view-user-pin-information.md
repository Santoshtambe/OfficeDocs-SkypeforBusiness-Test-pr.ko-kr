﻿---
title: 사용자 PIN 정보 보기
TOCTitle: 사용자 PIN 정보 보기
ms:assetid: 59e38117-8112-4851-82ac-a746ffa0f89d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688067(v=OCS.15)
ms:contentKeyID: 49885778
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 사용자 PIN 정보 보기

 

_**마지막으로 수정된 항목:** 2013-02-23_

AD DS(Active Directory 도메인 서비스) 자격 증명이 있는 Lync Server 2013 사용자가 인증된 사용자로 전화 접속 회의에 참가하려면 PIN(개인 식별 번호)이 필요합니다. Lync Server 2013 제어판에서 사용자의 PIN 정보를 볼 수 있습니다.


> [!NOTE]
> PIN이 설정되었는지 여부 또는 PIN이 마지막으로 변경된 시간 등의 PIN 상태 정보를 볼 수 있지만 PIN 상태로 조회해서 현재 PIN을 볼 수는 없습니다. 사용자가 자신의 PIN을 분실한 경우 <A href="lync-server-2013-set-a-user-s-dial-in-conferencing-pin.md">Lync Server 2013에서 사용자의 전화 접속 회의 PIN 설정</A>의 절차에 따라 다시 설정할 수 있습니다.



## Lync Server 제어판에서 사용자의 PIN을 잠그려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **사용자**를 클릭합니다.

4.  다음 방법 중 하나를 통해 사용자를 찾습니다.
    
      - **사용자 검색** 상자에 사용자 계정의 표시 이름, 이름, 성, SAM(보안 계정 관리자) 계정 이름, SIP 주소 또는 줄 URI(Uniform Resource Identifier)를 모두 또는 처음 부분을 입력하고 **찾기**를 클릭합니다.
    
      - 저장된 쿼리가 있는 경우 **쿼리 열기** 아이콘을 클릭하고 **열기** 대화 상자를 통해 쿼리(예: .usf 파일)를 검색한 후에 **찾기**를 클릭합니다.

5.  (선택 사항) 추가 검색 조건을 지정하여 결과 범위를 좁힙니다.
    
    1.  **필터 추가**를 클릭합니다.
    
    2.  사용자 속성을 입력하거나 드롭다운 목록의 화살표를 클릭하여 사용자 속성을 선택합니다.
    
    3.  **같음** 드롭다운 목록에서 연산자(예: **같음** 또는 **같지 않음**)를 클릭합니다.
    
    4.  선택한 사용자 속성에 따라 검색 결과를 필터링하는 데 사용할 조건을 직접 입력하거나 드롭다운 목록에서 화살표를 클릭하여 입력합니다.
        

        > [!TIP]
        > 쿼리에 검색 절을 더 추가하려면 <STRONG>필터 추가</STRONG>를 클릭합니다.

    
    5.  **찾기**를 클릭합니다.
    

    > [!NOTE]
    > PIN이 잠겨 있는 경우에는 PIN 잠금을 해제해야 설정할 수 있습니다. PIN 잠금을 해제하려면 사용자를 클릭하고 <STRONG>동작</STRONG>을 클릭한 후에 <STRONG>PIN 잠금 해제</STRONG>를 클릭합니다.



6.  검색 결과에서 사용자를 클릭하고 **동작**을 클릭한 후에 **PIN 상태 보기**를 클릭합니다.

## Lync Server 관리 셸 cmdlet을 사용하여 사용자 PIN 정보를 보려면

Get-CsClientPinInfo cmdlet을 사용하여 사용자 PIN 정보를 볼 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸에서 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 사용자 PIN 정보를 보려면

  - 사용자의 PIN 정보를 보려면 Lync Server 관리 셸에 다음과 비슷한 명령을 입력한 후 Enter 키를 누릅니다.
    
        Get-CsClientPinInfo -Identity "Ken Myer"
    
    그러면 다음과 비슷한 정보가 표시됩니다.
    
        Identity          : sip:kenmyer@litwareinc.com
        IsPinSet          : False
        IsLockedOut       : False
        LastPinChangeTime : 9/25/2012 1:35:03 PM
        PinExpirationTime :

자세한 내용은 [Get-CsConferenceDisclaimer](get-csconferencedisclaimer.md) cmdlet의 도움말 항목을 참조하십시오.

## 참고 항목

#### 작업

[Lync Server 2013에서 사용자의 전화 접속 회의 PIN 설정](lync-server-2013-set-a-user-s-dial-in-conferencing-pin.md)  
[사용자 PIN 잠금 또는 잠금 해제](lync-server-2013-lock-or-unlock-a-user-pin.md)

