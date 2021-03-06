﻿---
title: 회의 부하 분산
TOCTitle: 회의 부하 분산
ms:assetid: 5901a076-1b6f-4720-8837-95fc7f3c37f3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204922(v=OCS.15)
ms:contentKeyID: 49303712
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 회의 부하 분산

 

_**마지막으로 수정된 항목:** 2012-10-22_

다른 전용 회의 솔루션과 달리 Lync Server 아키텍처는 공유 하드웨어 모델입니다. 즉, 각각 여러 가지 실시간 통신을 지원하는 여러 소프트웨어 구성 요소에서 동일한 하드웨어를 공유합니다. 각 유형의 실시간 통신은 서버에 특정 부하를 줍니다. 예를 들어 프런트 엔드 서버는 SIP(Session Initiation Protocol) 라우팅 구성 요소, 웹 응용 프로그램(예: 주소록 검색), 웹 회의 서비스, A/V 회의 서비스, Enterprise Voice 응용 프로그램(예: 회의 길잡이 응용 프로그램 및 응답 그룹 응용 프로그램) 및 중재 서버를 실행할 수 있습니다. 프런트 엔드 서버의 데이터베이스 집합은 또한 저장소를 제공하고 사용자, 연락처, 현재 상태, 회의 및 음성 라우팅 데이터 처리를 지원합니다. 이러한 하드웨어 공유에서는 구성 요소, 서비스 및 프로세스가 CPU 및 메모리 리소스를 경합하므로 비회의 작업 부하는 서버 확장에 직접적인 영향을 주지 않습니다.

다른 하드웨어 포트 기반 회의 솔루션과 달리 Lync Server 회의 아키텍처는 비예약 모델입니다. 사용자가 모임을 예약할 때 Lync Server는 회의 데이터가 저장된 레코드를 회의 데이터베이스에 만들지만 예약된 모임을 위한 하드웨어 리소스를 미리 예약하지 않습니다. 대신 Lync Server에는 풀의 모든 프런트 엔드 서버에서 부하를 고르게 분산하는 방식으로 프런트 엔드 서버에 회의 리소스를 동적으로 할당하는 부하 분산 논리가 내장되어 있습니다. 이러한 방식으로 하드웨어 리소스를 효율적으로 프로비전하고 활용할 수 있지만 특히 적합한 계획이 없을 경우 대규모 모임을 지원하는 데에는 어려움이 있습니다. 예를 들어 Lync Server 2013 풀이 해당 최고 용량에 근접하게 실행되는 경우 각 프런트 엔드 서버는 약 125개의 평균 크기 모임을 호스팅할 수 있습니다. 몇 개의 소규모 모임을 추가하는 것은 문제가 되지 않지만 사용자 수가 1000명인 모임을 추가하면 프런트 엔드 서버에서 다른 125개의 모임과 함께 동시에 그러한 대규모 모임을 지원할 수 없을 것이기 때문에 문제가 될 수 있습니다.

