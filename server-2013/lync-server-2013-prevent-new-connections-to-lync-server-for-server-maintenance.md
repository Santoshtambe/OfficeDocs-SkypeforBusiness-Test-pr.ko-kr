﻿---
title: 서버 유지 관리를 위한 Lync Server의 새 연결 금지
TOCTitle: 서버 유지 관리를 위한 Lync Server의 새 연결 금지
ms:assetid: 22b27adf-a590-43bd-9306-a5789ae108d7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg520964(v=OCS.15)
ms:contentKeyID: 49303052
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 서버 유지 관리를 위한 Lync Server의 새 연결 금지

 

_**마지막으로 수정된 항목:** 2012-11-01_

Lync Server에서는 소프트웨어 또는 하드웨어 업그레이드를 적용하려는 등의 경우 사용자에게 서비스는 계속 제공하면서 서버를 오프라인으로 설정할 수 있습니다.

풀의 서버에 대한 새 연결 또는 통화를 방지하기 위한 옵션을 지정하면 이 옵션을 구현하는 즉시 새 연결 및 통화 수행이 중지됩니다. 이러한 새 연결 및 통화는 풀의 다른 서버를 통해 라우팅됩니다. 새 연결을 방지하는 서버는 기존 연결의 세션을 자연적으로 종료될 때까지 둡니다. 모든 기존 세션이 종료되면 서버를 오프라인으로 설정할 수 있습니다.

프런트 엔드 서버에 대한 새 연결을 방지하면 일부 Lync Server 기능 및 서비스는 DNS 부하 분산을 사용하여 이 옵션이 올바르게 작동하도록 합니다. 풀에서 DNS 부하 분산을 사용하지 않는 경우, 이러한 서비스를 통한 연결이 서버가 새 연결을 방지하는 기간 동안 다른 서버로 다시 라우팅되지 않아 서버가 오프라인으로 설정될 때 일부 세션 및 통화가 중단될 수 있습니다. 이 옵션이 적절하게 작동하도록 하기 위해 DNS 부하 분산을 사용하는 기능은 다음과 같습니다.

  - Attendant

  - 회의 알림 응용 프로그램

  - 응답 그룹 응용 프로그램

  - 알림 응용 프로그램

  - 통화 대기 응용 프로그램

DNS 부하 분산에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013의 DNS 부하 분산](lync-server-2013-dns-load-balancing.md)을 참조하십시오.

Lync Server를 실행하는 서버에서 모든 서비스에 대해 새 연결을 방지하는 것 외에, 개별 Lync Server 서비스에 대해서도 새 연결을 방지할 수 있습니다. 예를 들어 전체 서버를 종료하지 않아도 되는 Lync Server 업데이트를 적용해야 하는 경우에는 이 방법이 유용합니다. 특정 서비스에 대한 연결을 방지할 때는 Windows 서비스 목록에서 그룹화되어 표시되는 서비스를 선택해야 합니다. 예를 들어 모니터링용 데이터 수집 에이전트 및 Lync Server 프런트 엔드 서비스는 각각 별도의 Lync Server 서비스이지만, Windows 서비스 목록에는 Lync Server 프런트 엔드 서비스로 통합되어 표시됩니다. Lync Server 프런트 엔드 서비스에 대한 새 연결을 방지할 수는 있지만, 이러한 두 개별 기본 Lync Server 서비스에 대한 새 연결을 따로 방지할 수는 없습니다.


> [!IMPORTANT]
> 새 연결을 차단하도록 서버를 설정한 후에 서버를 다시 시작하면 기본적으로 서버가 시작된 직후 새 연결을 허용하기 시작합니다. 이러한 현상을 방지하려면 서버를 다시 시작하기 전에 서버를 수동으로만 일시 중지 및 다시 시작하도록 설정합니다.



## Lync Server에 대한 새 연결을 차단하려면

1.  Administrators 그룹의 구성원으로 로컬 컴퓨터에 로그온합니다.

2.  서비스 스냅인 콘솔을 엽니다. 그런 후에 **시작**을 클릭하고 **모든 프로그램**, **관리 도구**를 차례로 가리킨 다음 **서비스**를 클릭합니다.

3.  목록에서 새 연결을 차단할 Lync Server Windows 서비스를 두 번 클릭합니다.

4.  속성 페이지의 **서비스 상태: 시작됨**에서 **일시 중지**를 클릭합니다.

5.  원하는 경우 **시작 유형** 옆의 **수동**을 클릭합니다(권장).
    

    > [!IMPORTANT]
    > 새 연결을 차단하도록 서버를 설정한 후에 서버를 다시 시작하면 기본적으로 서버가 시작된 직후 새 연결을 허용하기 시작합니다. 이러한 현상을 방지하려면 서버를 다시 시작하기 전에 서버를 수동으로만 일시 중지 및 다시 시작하도록 설정합니다.



6.  작업을 마쳤으면 **확인**을 클릭합니다.
