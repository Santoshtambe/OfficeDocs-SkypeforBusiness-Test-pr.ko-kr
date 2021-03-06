﻿---
title: 'Lync Server 2013: 파일 공유 고가용성'
TOCTitle: 파일 공유 고가용성
ms:assetid: b8c8d5ec-9397-4128-8d1e-8ec6c30fade7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205203(v=OCS.15)
ms:contentKeyID: 49304832
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 파일 공유 고가용성

 

_**마지막으로 수정된 항목:** 2012-03-30_

한 데이터 센터 내에서 Lync Server 파일 공유의 고가용성을 보장하기 위해 DFS(분산 파일 시스템)를 사용할 수 있습니다. DFS는 한 파일 서버에서 동일한 데이터 센터 내에 있는 다른 파일 서버로의 장애 조치(failover)를 지원합니다. 대규모 배포의 경우 DFS를 사용하여 한 쌍으로 구성한 전용 파일 서버를 사용하는 것이 좋습니다.

네트워크 규모와 원하는 복원력 수준에 따라 한 쌍의 서버로 사이트의 모든 파일 공유를 호스팅할 수도 있고 프런트 엔드 풀당 한 쌍의 서버를 사용할 수도 있습니다.

DFS는 공표된 RTO(복구 시간 목표) 또는 RPO(복구 시점 목표)가 없는 "최상의 노력" 파일 복제 메커니즘입니다. DFS 서버 간의 장애 조치는 신속하게 완료되겠지만 데이터 복제 지연으로 장애 조치 도중에 사용자가 작업을 계속 진행하지 못할 수 있습니다.

DFS를 사용하고 있으며 파일 공유 데이터 저장소가 중요한 경우 파일 공유를 자주(예: 4~8시간마다) 백업해야 합니다. 한 파일 공유가 다운되고 복제가 최신 상태가 아닌 경우 백업을 사용하여 장애가 발생한 서버의 콘텐츠를 현재 사용할 수 없는 서버와 한 쌍으로 구성된 다른 서버로 복원할 수 있습니다.

