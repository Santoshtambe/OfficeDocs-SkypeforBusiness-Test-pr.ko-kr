﻿---
title: 'Lync Server 2013: Standard Edition 서버에 대한 DNS 요구 사항'
TOCTitle: Standard Edition 서버에 대한 DNS 요구 사항
ms:assetid: 5d1daf54-6e60-4ce0-9254-7d57a0835fa4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204936(v=OCS.15)
ms:contentKeyID: 49303768
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 Standard Edition 서버에 대한 DNS 요구 사항

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 섹션에서는 Standard Edition 서버를 배포하는 데 필요한 DNS(Domain Name System) 레코드에 대해 설명합니다.

## Standard Edition 서버에 대한 DNS 레코드

다음 표에서는 Lync Server 2013 Standard Edition 서버 배포에 대한 DNS 요구 사항을 지정합니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>배포 시나리오</th>
<th>DNS 요구 사항</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Standard Edition 서버</p></td>
<td><p>서버의 FQDN(정규화된 도메인 이름)을 IP 주소로 확인하는 내부 A 레코드</p></td>
</tr>
<tr class="even">
<td><p>자동 클라이언트 로그인</p></td>
<td><p>지원되는 각 SIP 도메인에 대해 로그인을 위한 클라이언트 요청을 인증하고 리디렉션하는 Standard Edition 서버의 FQDN에 매핑되는 _sipinternaltls._tcp.&lt;도메인&gt;(포트 5061)에 대한 SRV 레코드. 자세한 내용은 <a href="lync-server-2013-dns-requirements-for-automatic-client-sign-in.md">Lync Server 2013의 자동 클라이언트 로그인에 대한 DNS 요구 사항</a>을 참고하세요.</p></td>
</tr>
<tr class="odd">
<td><p>UC(통합 통신) 장치를 통한 장치 업데이트 웹 서비스 검색</p></td>
<td><p>장치 업데이트 웹 서비스를 호스팅하는 Standard Edition 서버의 IP 주소로 확인되는 ucupdates-r2.&lt;SIP 도메인&gt; 이름의 내부 A 레코드. UC 장치가 설정되었지만 사용자가 장치에 로그인하지 않은 상황에서 A 레코드를 사용하면 장치가 장치 업데이트 웹 서비스를 호스팅하는 서버를 검색하고 업데이트를 가져올 수 있습니다. 그렇지 않은 경우 장치는 사용자가 처음 로그인할 때 인밴드 프로비전을 통해 해당 서버 정보를 가져옵니다. 자세한 내용은 작업 설명서에서 <a href="lync-server-2013-device-update-web-service.md">Lync Server 2013의 장치 업데이트 웹 서비스</a>를 참고하세요.</p></td>
</tr>
<tr class="even">
<td><p>HTTP 트래픽을 지원하는 역방향 프록시</p></td>
<td><p>외부 웹 팜 FQDN을 역방향 프록시의 외부 IP 주소로 확인하는 외부 A 레코드. 클라이언트와 UC 장치는 이 레코드를 사용하여 역방향 프록시에 연결합니다. 자세한 내용은 계획 설명서에서 <a href="lync-server-2013-determine-dns-requirements.md">Lync Server 2013에 대한 DNS 요구 사항 확인</a>을 참조하십시오.</p></td>
</tr>
</tbody>
</table>


## 참고 항목

#### 개념

[Lync Server 2013의 자동 클라이언트 로그인에 대한 DNS 요구 사항](lync-server-2013-dns-requirements-for-automatic-client-sign-in.md)  
[Lync Server 2013에 대한 DNS 요구 사항 확인](lync-server-2013-determine-dns-requirements.md)  

#### 기타 리소스

[Lync Server 2013의 장치 업데이트 웹 서비스](lync-server-2013-device-update-web-service.md)

