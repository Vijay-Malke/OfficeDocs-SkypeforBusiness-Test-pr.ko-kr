﻿---
title: 'Lync Server 2013: 위치를 수동으로 가져오기 위한 사용자 환경 정의'
TOCTitle: 위치를 수동으로 가져오기 위한 사용자 환경 정의
ms:assetid: d37f67d3-e248-483b-b64c-3986559ef357
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398912(v=OCS.15)
ms:contentKeyID: 49305135
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 위치를 수동으로 가져오기 위한 사용자 환경 정의

 

_**마지막으로 수정된 항목:** 2012-10-03_

클라이언트가 네트워크 외부에 있거나 정의되지 않은 서브넷에 있는 경우 사용자가 위치를 수동으로 입력할 수 있습니다. 하지만 긴급 통화 시 통화는 PSAP(Public Safety Answering Point)로 라우팅되기 전에 국가/지역 E9-1-1 ECRC(Emergency Call Response Center) 발송자로 먼저 라우팅됩니다. ECRC는 구두로 발신자에게 위치를 문의한 후 제공된 정보에 따라 적합한 PSAP로 통화를 전달합니다.

  - **위치 정보 서비스에서 위치가 자동으로 제공되지 않는 경우 사용자에게 위치를 입력하라는 메시지를 표시해야 합니까?**  
    예를 들어 클라이언트가 정의되지 않은 서브넷, 집, 호텔 또는 네트워크 외부 지역에 있는 경우 사용자가 위치를 입력해야 합니까?
    
    위치 정책에서 **위치 필요** 설정을 구성하여 클라이언트 동작을 정의할 수 있습니다. 이 값을 아니요로 설정하면 사용자에게 위치를 입력하라는 메시지가 표시되지 않습니다. 반면 예로 설정하면 사용자에게 위치를 입력하라는 메시지가 표시되며, 이 메시지는 취소할 수 있습니다. 이 값을 고지 사항으로 설정하면 사용자에게 위치를 입력하라는 메시지가 표시되고, 메시지를 취소할 때 고지 사항이 표시됩니다. 어느 옵션을 선택해도 사용자는 평소와 같이 클라이언트를 계속 사용할 수 있습니다.

사용자가 위치를 수동으로 입력하면 클라이언트 네트워크의 기본 게이트웨이에 대한 MAC 주소로 위치가 매핑되고 클라이언트에 있는 사용자별 테이블에 저장됩니다. 사용자가 이전에 저장된 위치로 돌아가면 Lync 클라이언트가 자동으로 해당 위치로 설정됩니다.


> [!NOTE]
> 클라이언트의 현재 위치만 수정할 수 있지만 로컬 사용자의 테이블에 저장된 어느 위치든 삭제할 수 있습니다.


