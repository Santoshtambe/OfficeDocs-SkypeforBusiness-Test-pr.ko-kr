﻿---
title: 'Lync Server 2013: Validating voice number normalization and routing'
TOCTitle: Validating voice number normalization and routing
ms:assetid: a6a825c7-6928-4e80-b7e9-803b7f7ebd13
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn720922(v=OCS.15)
ms:contentKeyID: 62240124
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Validating voice number normalization and routing in Lync Server 2013

 

_**마지막으로 수정된 항목:** 2014-05-19_

Correct number normalization and routing is very important for functional Enterprise Voice environment. Especially during migrations from private branch exchange (PBX) to stand-alone Lync Server environment, one of the keys to successful migration is to reveal and document all existing dialing rules, and create appropriate normalization rules, voice policies, phone usages and routes.

Validating number normalization and routing is important not only during migrations but also during normal, stable operation of the system.

We recommend conducting this validation daily by using the Lync Server 제어판, starting with developing a robust set of test cases against the current set of normalization rules that were published in the Lync Server global settings. These test cases should be run daily to highlight any unwanted changes that were made and committed to the dial plan.

Lync Server 제어판 also helps you visualize, test, change, archive, and share configuration information about voice routing and in changing Enterprise Voice number normalization rules, dial plans, voice policy, and routes. It has additional features for doing the following:

  - Exporting and importing or backing up voice routing data between systems.

  - Testing configuration changes before uploading them to a live system.

  - Creating and running configuration test cases to help ensure the usability of routing data after you make changes to it, but before committing them the changes to a deployed system.

  - Creating and changing number normalization rules, location profiles, voice policy, and routing data without writing the necessary regular expressions.

  - Analyzing a location profile for compatibility with the Lync Server Phone Edition.

  - More information about voice routing tests can be found at [Lync Server 2013에서 음성 라우팅 테스트](lync-server-2013-test-voice-routing.md)

## 참고 항목

#### 기타 리소스

[Lync Server 2013에서 음성 라우팅 테스트](lync-server-2013-test-voice-routing.md)

