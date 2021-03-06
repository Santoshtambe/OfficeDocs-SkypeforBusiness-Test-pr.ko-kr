﻿---
title: 'Lync Server 2013: 통화 대기 번호 테이블 구성'
TOCTitle: 통화 대기 번호 테이블 구성
ms:assetid: e5cc0c19-7b2c-48e7-a21d-cfb23c842f0f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399020(v=OCS.15)
ms:contentKeyID: 49305340
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 통화 대기 번호 테이블 구성

 

_**마지막으로 수정된 항목:** 2012-09-10_

통화 대기에서는 파킹된 통화 번호를 사용하여 통화를 대기시킵니다. 통화 대기 파킹된 통화 번호 테이블을 구성해야 사용자가 통화를 대기시키고 재개할 수 있습니다. 조직에서 통화 대기를 위해 예약하고 각 범위를 처리하는 통화 대기 풀을 지정하여 해당 범위에 대한 라우팅을 정의하는 내선 번호(파킹된 통화 번호) 범위를 지정해야 합니다. 파킹된 통화 번호 범위를 정의하는 목표는 파킹된 통화 번호를 충분히 확보하여 파킹된 특정 통화 번호가 너무 빨리 재사용되지 않도록 하고 사용자나 다른 서비스에서 사용할 수 있는 내선 번호 수를 제한하는 파킹된 통화 번호 수가 너무 많지 않도록 하는 것입니다. 통화 대기 응용 프로그램가 배포된 각 Lync Server 풀에 대해 여러 개의 통화 대기 파킹된 통화 번호 범위를 만들 수 있습니다. 각 통화 대기 파킹된 통화 번호 범위에는 전역적으로 고유한 이름과 고유한 내선 번호 집합이 있어야 합니다.


> [!IMPORTANT]
> 파킹된 통화 번호 범위에는 일반적으로 100개 이하의 파킹된 통화 번호가 포함됩니다. 각 범위는 범위당 최대값인 10,000개의 파킹된 통화 번호보다 범위가 작고 풀당 50,000개 미만의 파킹된 통화 번호가 있는 경우 훨씬 커질 수 있습니다. 범위가 너무 작으면 파킹된 통화 번호가 보다 빠르게 재사용될 수 있습니다.



파킹된 통화 번호 범위에 대해 가상 내선 번호 블록(사용자나 전화가 할당되지 않은 내선 번호)을 사용합니다.


> [!NOTE]
> DID(Direct Inward Dialing) 번호를 통화 대기 파킹된 통화 번호 테이블에서 파킹된 통화 번호로 할당할 수는 없습니다.



## 이 단원의 내용

[Lync Server 2013에서 통화 대기 번호 범위 만들기 또는 수정](lync-server-2013-create-or-modify-a-call-park-orbit-range.md)

