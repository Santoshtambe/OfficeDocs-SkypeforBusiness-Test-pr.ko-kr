﻿---
title: 사이트 및 지역 정보를 사용하도록 Lync Server 2013에서 미디어 바이패스 전역 설정 구성
TOCTitle: 사이트 및 지역 정보를 사용하도록 Lync Server 2013에서 미디어 바이패스 전역 설정 구성
ms:assetid: 0a21cdf1-f350-49da-b346-70806f256bea
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398150(v=OCS.15)
ms:contentKeyID: 49302754
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 사이트 및 지역 정보를 사용하도록 Lync Server 2013에서 미디어 바이패스 전역 설정 구성

 

_**마지막으로 수정된 항목:** 2012-09-21_


> [!NOTE]
> 이 항목에서는 중재 서버 미디어 바이패스를 설정하려는 특정 사이트 또는 서비스에 대해 중재 서버에서 피어(ITSP(인터넷 전화 통신 서비스 공급자)의 공중 전화망(PSTN) 게이트웨이, IP-PBX 또는 SBC(Session Border Controller))로의 트렁크 연결에 대한 미디어 바이패스를 이미 구성한 것으로 가정합니다.<BR>또한 이 항목에서는 <A href="lync-server-2013-create-or-modify-a-network-region.md">Lync Server 2013에서 네트워크 지역 만들기 또는 수정</A>, <A href="lync-server-2013-create-or-modify-a-network-site.md">Lync Server 2013에서 네트워크 사이트 만들기 또는 수정</A> 및 <A href="lync-server-2013-associate-a-subnet-with-a-network-site.md">Lync Server 2013 에서 네트워크 사이트에 서브넷 연결</A>에 설명된 단계에 따라 수행한 네트워크 지역, 네트워크 사이트 및 서브넷 구성과 일치하는 방식으로 토폴로지 작성기의 모든 중앙 사이트 및 분기 사이트를 정의한 것으로 가정합니다. 구성이 일치하지 않으면 미디어 바이패스에 실패합니다.



피어와 연결된 개별 트렁크 연결에 대한 미디어 바이패스를 설정하는 것 외에 전역 설정도 구성해야 합니다. 이 항목의 단계를 사용하여 미디어 바이패스에 대한 전역 설정을 구성하는 경우 다음 상황 중 하나 또는 둘 다가 구성에 영향을 주는 것으로 가정합니다.

  - Lync Server 끝점과 트렁크 연결에 대한 미디어 바이패스를 구성한 피어 간의 연결이 양호하지 *않은 경우*

  - 대역폭 관리에 대한 CAC(통화 허용 제어)가 설정된 경우
    

    > [!NOTE]
    > 통화 허용 제어 및 미디어 바이패스에 대한 자세한 고려 사항은 계획 설명서의 <A href="lync-server-2013-media-bypass-and-mediation-server.md">Lync Server 2013의 미디어 바이패스 및 중재 서버</A>에서 "PSTN 연결의 통화 허용 제어" 섹션을 참조하십시오.



네트워크 지역 및 네트워크 사이트 정보는 통화 허용 제어와 미디어 바이패스 고급 Enterprise Voice 기능 간에 공유됩니다(둘 다 설정된 경우). 따라서 통화 허용 제어를 이미 구성한 경우 다음 절차에 따라 특별히 미디어 바이패스에 대해 사이트 및 지역 정보를 편집할 필요가 없습니다. 통화 허용 제어에 대한 네트워크 지역 및 사이트를 아직 구성하지 않은 상태에서 미디어 바이패스 설정을 변경하려는 경우에 이 절차의 단계를 따르십시오.

또는 미디어 바이패스에 대한 결정을 내릴 때 사이트 및 지역 정보를 사용하되, 통화 허용 제어를 설정하지 않으려는 경우에 이러한 단계를 따르십시오. 이 경우에는 [Lync Server 2013에서 새 네트워크 사이트 간 정책 만들기](lync-server-2013-create-network-intersite-policies.md)에 설명된 대로 네트워크 사이트 간 정책을 통해 대역폭이 제한된 링크를 표시해야 합니다. 통화 허용 제어가 설정되지 않았으므로 이 경우 실제 대역폭 제한은 중요하지 않습니다. 대신, 이러한 링크는 서브넷을 분할하여 대역폭 제한이 없는 링크를 지정하는 데 사용되므로 미디어 바이패스를 적용할 수 있습니다. 이는 통화 허용 제어와 미디어 바이패스가 둘 다 설정된 경우에도 마찬가지입니다.

또한 미디어 바이패스가 제대로 작동하려면 토폴로지 작성기에 정의된 사이트와 네트워크 지역 및 네트워크 사이트를 구성할 때 정의한 사이트 간에 일관성이 유지되어야 합니다. 예를 들어 토폴로지 작성기의 분기 사이트를 PSTN 게이트웨이만 배포된 것으로 정의한 경우 분기 사이트는 해당 사용자가 PSTN 통화를 분기 사이트의 PSTN 게이트웨이를 통해 라우팅할 수 있도록 지원하는 Enterprise Voice 정책을 사용하여 구성되어야 합니다.

## 미디어 바이패스에 대한 사이트 및 지역 정보를 구성하려면

1.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

2.  왼쪽 탐색 모음에서 **네트워크 구성**을 클릭합니다.

3.  테이블에서 **전역** 구성을 두 번 클릭합니다.

4.  **전역 설정 편집** 페이지에서 **미디어 바이패스 사용** 확인란을 선택합니다.

5.  **사이트 및 지역 구성 사용**을 클릭합니다.

6.  필요한 경우 **매핑되지 않은 사이트에 대해 바이패스 사용** 확인란을 선택합니다.
    

    > [!NOTE]
    > 이 확인란은 대역폭 제한이 없는 하나 이상의 큰 사이트(예: 대규모 중앙 사이트)를 같은 지역과 연결했지만 대역폭이 제한된 일부 분기 사이트도 이 지역과 연결한 경우에만 선택합니다. 매핑되지 않은 사이트에 대해 바이패스를 사용하도록 설정하면 모든 사이트와 연결된 모든 서브넷을 지정할 필요 없이 분기 사이트와 연결된 서브넷만 지정하면 되므로 구성이 간소화됩니다. 통화 허용 제어가 설정된 경우에는 이 확인란을 선택하지 않는 것이 좋습니다.



7.  **커밋**을 클릭합니다.

다음으로, [미디어 바이패스를 위해 네트워크 사이트에 서브넷 연결](lync-server-2013-associate-subnets-with-network-sites-for-media-bypass.md)에 설명된 대로 네트워크 사이트에 서브넷을 추가합니다. 서브넷을 네트워크 사이트와 연결하는 실제 절차는 [Lync Server 2013 에서 네트워크 사이트에 서브넷 연결](lync-server-2013-associate-a-subnet-with-a-network-site.md)에 설명되어 있습니다. 모든 서브넷을 네트워크 사이트와 연결하면 미디어 바이패스 배포가 완료됩니다.


> [!IMPORTANT]
> 네트워크 지역 및 네트워크 사이트를 아직 만들지 않은 경우 미디어 바이패스 배포를 진행하려면 먼저 네트워크 지역과 네트워크 사이트를 만들어야 합니다. 자세한 내용은 <A href="lync-server-2013-create-or-modify-a-network-region.md">Lync Server 2013에서 네트워크 지역 만들기 또는 수정</A> 및 <A href="lync-server-2013-create-or-modify-a-network-site.md">Lync Server 2013에서 네트워크 사이트 만들기 또는 수정</A>을 참조하십시오.



## 참고 항목

#### 개념

[미디어 바이패스를 위해 네트워크 사이트에 서브넷 연결](lync-server-2013-associate-subnets-with-network-sites-for-media-bypass.md)

