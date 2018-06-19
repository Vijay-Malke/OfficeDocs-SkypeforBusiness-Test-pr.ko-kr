﻿---
title: 'Lync Server 2013: 영구 채팅 서버에 필요한 리소스'
TOCTitle: 필요한 리소스
ms:assetid: bce50b95-f3c8-407e-963a-d8896ee77fbc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205211(v=OCS.15)
ms:contentKeyID: 49304871
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 영구 채팅 서버에 필요한 리소스

 

_**마지막으로 수정된 항목:** 2013-11-01_

영구 채팅 서버의 고가용성 및 재해 복구를 위해서는 완전한 작동에 일반적으로 필요한 리소스 이외에 추가 리소스가 필요합니다. 고가용성 및 재해 복구를 위해 영구 채팅 서버를 구성하는 경우 먼저 표준 영구 채팅 서버 작동에 필요한 리소스 이외에 다음 리소스를 갖추었는지 확인합니다. 자세한 구성 정보는 [Lync Server 2013에서 영구 채팅 서버 구성](lync-server-2013-configuring-persistent-chat-server.md)을 참조하십시오.

  - 영구 채팅 서버 서비스의 홈 프런트 엔드와 동일한 실제 데이터 센터에 있는 전용 데이터베이스 인스턴스 하나. 이 데이터베이스는 주 영구 채팅 데이터베이스의 SQL Server 미러로 작동합니다. 또한 이 미러 데이터베이스에 대한 자동 장애 조치(failover)를 원할 경우 미러링 모니터로 작동할 추가 SQL Server를 지정합니다.

  - 다른 실제 데이터 센터에 있는 전용 데이터베이스 인스턴스 하나. 이 데이터베이스는 주 데이터 센터에 있는 데이터베이스의 SQL Server 로그 전달 보조 데이터베이스로 작동합니다.

  - 보조 데이터베이스의 SQL Server 미러로 작동할 전용 데이터베이스 인스턴스 하나. 필요에 따라 미러링 모니터로 작동할 추가 SQL Server를 지정합니다. 이 두 가지 모두 보조 데이터베이스와 동일한 실제 데이터 센터에 있어야 합니다.

  - 영구 채팅 서버 준수를 사용하도록 설정한 경우 추가로 3개의 전용 데이터베이스 인스턴스가 필요합니다. 이러한 인스턴스의 배포는 영구 채팅 데이터베이스에 대해 앞에서 설명한 것과 동일합니다. 준수 데이터베이스는 영구 채팅 데이터베이스와 동일한 SQL Server 인스턴스를 공유할 수 있지만 고가용성과 재해 복구를 위해 독립 실행형 인스턴스를 사용하는 것이 좋습니다.

  - 또한 SQL Server 로그 전달 트랜잭션 로그를 위한 파일 공유를 만들고 지정해야 합니다. 영구 채팅 데이터베이스를 실행하는 두 데이터 센터에 있는 모든 SQL Server에는 이 파일 공유에 대한 읽기/쓰기 권한이 있어야 합니다. 이 공유는 FileStore 역할의 일부로 정의되지 않습니다.

  - 주 서버 파일 공유에서 복사되는 SQL Server 트랜잭션 로그의 대상 폴더로 작동할 보조 데이터베이스 서버의 파일 공유

다음 그림에서는 전체 영구 채팅 서버 풀을 두 가지 확장 풀 토폴로지로 구성할 수 있는 방법에 대한 예를 제공합니다.

  - 데이터 센터가 높은 대역폭/짧은 대기 시간을 사용하여 지리적으로 분산된 경우의 확장 영구 채팅 서버 풀

  - 데이터 센터가 낮은 대역폭/긴 대기 시간을 사용하여 지리적으로 분산된 경우의 확장 영구 채팅 서버 풀

다음 그림에서는 데이터 센터가 높은 대역폭/짧은 대기 시간을 사용하여 지리적으로 분산된 경우의 확장 영구 채팅 서버 풀 토폴로지를 보여 줍니다.

**데이터 센터가 높은 대역폭/짧은 대기 시간을 사용하여 지리적으로 분산된 경우의 확장 영구 채팅 서버 풀**

![영구 채팅 서버 풀 HBW 구성 검사](images/JJ205211.55d10910-c824-41e6-bed2-08d13a2abd65(OCS.15).jpg "영구 채팅 서버 풀 HBW 구성 검사")

다음 그림에서는 데이터 센터가 낮은 대역폭/긴 대기 시간을 사용하여 지리적으로 분산된 경우의 확장 영구 채팅 서버 풀 토폴로지를 보여 줍니다.

**데이터 센터가 낮은 대역폭/긴 대기 시간을 사용하여 지리적으로 분산된 경우의 확장 영구 채팅 서버 풀**

![영구 채팅 서버 풀 LBW 구성 검사](images/JJ205211.586b0a3a-3767-4991-944f-ee54389512aa(OCS.15).jpg "영구 채팅 서버 풀 LBW 구성 검사")
