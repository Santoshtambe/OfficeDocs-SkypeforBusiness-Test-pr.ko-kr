﻿---
title: 파일럿 풀로 여러 사용자 이동
TOCTitle: 파일럿 풀로 여러 사용자 이동
ms:assetid: 9492797f-2a26-4773-8ad2-97cb53fa68fc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688143(v=OCS.15)
ms:contentKeyID: 49885882
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 파일럿 풀로 여러 사용자 이동

 

_**마지막으로 수정된 항목:** 2012-10-02_

Lync Server 2013 제어판 또는 Lync Server 2013 관리 셸을 사용하여 여러 사용자를 Office Communications Server 2007 R2 풀에서 Lync Server 2013 파일럿 풀로 이동할 수 있습니다.

## Lync Server 2013 제어판을 사용하여 여러 사용자를 이동하려면

1.  **Lync Server 제어판** 을 엽니다.

2.  **사용자 검색** 탭에서 **검색** 단추를 클릭합니다.

3.  그런 다음 **필터 추가**를 클릭합니다.

4.  **Office Communications Server 사용자**가 **True**와 같은 필터를 만듭니다.

5.  **찾기**를 클릭하여 기존 Office Communications Server 2007 R2 사용자를 검색합니다.

6.  Lync Server 2013 풀로 이동할 사용자 두 명을 선택합니다. 이 예에서는 사용자 Chen Yang과 Claus Hansen을 이동하겠습니다.
    
    ![OCS 사용자 검색 결과 표시된 사용자 목록](images/JJ688143.76beb4fa-72e0-41ef-b96e-3553e96645c0(OCS.15).jpg "OCS 사용자 검색 결과 표시된 사용자 목록")  

7.  **동작** 메뉴에서 **선택한 사용자를 풀로 이동** 을 선택합니다.

8.  드롭다운 목록에서 Lync Server 2013 풀을 선택합니다.

9.  **동작** , **선택한 사용자를 풀로 이동** , 확인을 차례로 클릭합니다.
    
    ![사용자 이동, 대상 등록자 풀 대화 상자](images/JJ205401.8a375003-dc00-4541-b578-4d88f2010601(OCS.15).png "사용자 이동, 대상 등록자 풀 대화 상자")  

10. 사용자의 **등록자 풀** 열에 이제 Lync Server 2013 풀이 포함되어 있는지 확인합니다. 포함되어 있으면 사용자가 성공적으로 이동된 것입니다.

## Lync Server 2013 관리 셸을 사용하여 여러 사용자를 이동하려면

1.  Lync Server 2013 관리 셸을 엽니다.

2.  명령줄에 다음을 입력하고 **User1** 및 **User2**를 이동하려는 특정 사용자 이름으로 바꾸고 **pool\_FQDN**을 대상 풀의 이름으로 바꿉니다. 이 예에서는 Hao Chen과 Katie Jordan을 이동하겠습니다.
    
        Get-CsUser -Filter {DisplayName -eq "User1" -or DisplayName - eq "User2"} | Move-CsLegacyUser -Target "pool_FQDN"
    
    ![레거시 사용자를 이동하는 cmdlet의 예제](images/JJ688143.57cfc28e-3df5-459f-83ef-8b0edf182a25(OCS.15).jpg "레거시 사용자를 이동하는 cmdlet의 예제")  

3.  명령줄에 다음을 입력합니다.
    
        Get-CsUser -Identity "User1"

4.  **등록자 풀** ID는 이제 사용자가 이전 단계에서 **pool\_FQDN**으로 지정한 풀을 가리킵니다.이 ID가 있으면 사용자가 성공적으로 이동된 것입니다. 이 단계를 반복하여 **User2**가 이동되었는지 확인합니다.
    
    ![PowerShell Get-UsUser -Identity cmdlet의 출력](images/JJ205096.8ff04c67-37a0-4156-bfbc-28f9f7b137c8(OCS.15).jpg "PowerShell Get-UsUser -Identity cmdlet의 출력")  

## Lync Server 2013 관리 셸을 사용하여 모든 사용자를 동시에 이동하려면

이 예에서는 모든 사용자가 Office Communications Server 2007 R2 풀(pool01.contoso.net)로 복귀되었습니다. Lync Server 2013 관리 셸을 사용하여 모든 사용자를 동시에 Lync Server 2013 풀(pool02.contoso.net)로 이동하겠습니다.

1.  **Lync Server 2013 관리 셸**을 엽니다.

2.  명령줄에 다음을 입력합니다.
    
        Get-CsUser -OnOfficeCommunicationServer | Move-CsLegacyUser -Target "pool_FQDN"
    
    ![풀의 모든 레거시 사용자를 이동하는 cmdlet의 예제](images/JJ688143.e6a2d578-296e-476c-bd45-d757917ea853(OCS.15).jpg "풀의 모든 레거시 사용자를 이동하는 cmdlet의 예제")  

3.  그런 다음 파일럿 사용자 한 명에 대해 **Get-CsUser**를 실행합니다.
    
        Get-CsUser -Identity "Hao Chen"

4.  각 사용자의 **등록자 풀** ID는 이제 사용자가 이전 단계에서 "pool\_FQDN"으로 지정한 풀을 가리킵니다. 이 ID가 있으면 사용자가 성공적으로 이동된 것입니다.

5.  또한 Lync Server 2013 제어판에서 사용자 목록을 보고 등록자 풀 값이 이제 Lync Server 2013 풀을 가리키는지 확인할 수도 있습니다.
    
    ![Lync Server 2013 제어판 사용자 목록](images/JJ205096.3f2e87a7-ec59-43c5-82cb-e770108bfb04(OCS.15).jpg "Lync Server 2013 제어판 사용자 목록")

