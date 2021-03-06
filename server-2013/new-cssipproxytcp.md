﻿---
title: New-CsSipProxyTCP
TOCTitle: New-CsSipProxyTCP
ms:assetid: 27600a10-cc00-4be0-ab47-0bb06e65e4cd
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425745(v=OCS.15)
ms:contentKeyID: 49303112
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsSipProxyTCP

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 SipProxy.TCP 개체를 만든 다음 이 개체를 사용하여 TCP(Transmission Control Protocol)를 전송 프로토콜로 사용하는 고정 경로를 구성할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsSipProxyTCP -IPAddress <String>

## 예제

## 예제 1

예제 1에 표시된 명령은 TCP를 전송 프로토콜로 사용하는 새 SIP 프록시 전송 개체를 만듭니다. 이를 위해 예제의 첫 번째 명령에서는 **New-CsSipProxyTCP** cmdlet을 사용하여 IP 주소 192.168.1.100으로 다음 홉 서버를 가리키는 새 SipProxy.TCP 개체를 만듭니다. 이 TCP 개체는 $tcp 변수에 저장됩니다.

SipProxy.TCP 개체가 만들어진 후 **New-CsSipProxyTransport** cmdlet이 TCP 전송 개체를 만듭니다.

    $tcp = New-CsSipProxyTCP -IPAddress 192.168.1.100
    
    $transport = New-CsSipProxyTransport -TransportChoice $tcp -Port 7500

## 자세한 정보

SIP 메시지를 누군가에게 보내는 경우 이 메시지는 배달되기 전에 여러 서브넷과 네트워크를 통과해야 할 수 있습니다. 메시지가 거치는 이러한 길을 일반적으로 경로라고 합니다. 네트워킹에는 동적 경로와 고정 경로의 두 가지 유형의 경로가 있습니다. 동적 경로의 경우 서버가 알고리즘을 사용하여 메시지를 전달할 다음 위치(다음 홉)을 결정합니다. 고정 경로의 경우 시스템 관리자가 메시지 경로를 미리 정합니다. 서버는 메시지를 수신하면 메시지 주소를 확인하고 관리자가 미리 구성한 다음 홉 서버로 메시지를 전달합니다. 고정 경로를 제대로 구성한 경우에는 제시간에 정확하게 메시지를 전달하고 서버에 대한 오버헤드를 최소화할 수 있습니다. 고정 경로의 단점은 네트워크 실패 시 메시지가 동적으로 다시 경로 지정되지 않는다는 것입니다.

Lync Server를 사용하여 프록시 서버의 고정 경로를 설정할 수 있습니다. 이러한 경로는 프록시 구성 설정(**New-CsProxyConfiguration** cmdlet을 사용하여 생성됨) 및 SIP 프록시 경로로 구성됩니다. SIP 프록시 경로에는 여러 속성이 있는데, 예를 들어 각 경로에는 경로를 따라 메시지를 전송하는 데 사용되는 네트워크 프로토콜을 정의하는 Transport 속성이 있어야 합니다.

Lync Server를 사용하면 TCP(Transmission Control Protocol) 또는 TLS(전송 계층 보안)를 전송 프로토콜로 지정할 수 있습니다. TCP를 프로토콜로 사용하도록 결정한 경우 먼저 **New-CsSipProxyTCP** cmdlet을 사용하여 TCP 개체를 만들어야 합니다. 그런 다음 이 개체를 사용하여 **New-CsSipProxyTransport** cmdlet으로 만든 Transport 개체의 프로토콜을 지정해야 합니다.

**New-CsStaticRoute** cmdlet을 사용하여 고정 경로를 만드는 경우 **New-CsSipProxyTCP** cmdlet을 사용할 필요가 없습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsSipProxyTCP** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsSipProxyTCP"}

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
<td><p><em>IPAddress</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>다음 홉 라우터의 IP 주소입니다 (예: -IPAddress 192.168.0.240).</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsSipProxyTCP** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsSipProxyTCP** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.TCP 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[New-CsSipProxyTLS](new-cssipproxytls.md)  
[New-CsSipProxyTransport](new-cssipproxytransport.md)

