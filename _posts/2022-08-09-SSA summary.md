---
title:  "SSA 개념 정리"
excerpt: ""

categories:
  - Blog
tags:
  - [SSA, AWS]

toc: true
toc_sticky: true
 
date: 2022-08-10
last_modified_at: 2022-08-10
---

1. LoadBalancer  
NLB : UDP/TCP
ALB : WAF 가능

2. 데이터 복제  
리전간 복제 = S3 교차 리전 복제 구성  

3. Global Accelarator  
어플리케이션의 성능 향상

4. 방화벽 정리  
   보안그룹 : 인스턴스단위/상태저장/허용만 설정 가능/인바운드 룰  
      Type : HTTP, HTTPS, SSH ...  
      Source : Anywhere, 특정IP, 다른 보안그룹   
   NACL : 서브넷단위/상태비저장/허용,거부 설정 가능
외부 웹 공격과 DDOS를 모두 막을 수 있는 최선의 솔루셥 2개 조합은?
WAF, Shiel+ GuardDuty (보기에 Shield with NLF, WAF with NLB 등 주의)

* AWS 의 기타 서비스  
• Cognito : 회원관리
• GuardDuty : 외부침입분석
• Inspector : 내부취약점분석
• Macie : 민감한 개인정보 관리 

5. S3
varing durations of time (S3가 알아서 저장소 관리를 --> S3 intelligent tiering)  
• S3 Standard(범용) - 3개의 가용영역에 데이터 저장, 자주 액세스하는 파일을 저장하는 데 사용  
• S3 Standard-IA (Standard Infrequent Access) - 3개의 가용영역에 데이터 저장, 자주 액세스하지 않는 파일을 저장하는 데 사용  
• One Zone IA (One Zone Infrequent Access) - 1개의 가용영역에 데이터 저장, 자주 액세스하지 않는 파일을 저장하는데 사용  
• S3 Intelligent-Tiering(지능형 계층화) 혹은 EFS 수명주기 관리 정책 - 액세스 패턴을 알 수 없거나 예측할 수 없는 데이터용, 액세스 패턴을 모니터링하고, 액세스하지 않은 객체를 저렴한 액세스 계층으로 자동으로 이동

기타 (아카이브용)
• Glacier Instant Retrieval - 분기에 한 번 액세스하는 오래된 아카이브 데이터 용도
• S3 Glacier/Glacier Flexible Retrieval - 일 년에 한 번 액세스하는 오래된 아카이브 데이터 용도
• S3 Glacier Deep Archive - 일 년에 한 번 미만으로 액세스하는 오래된 아카이브 데이터 용도

6. EC2
예측가능한 용량 및 시간 ==> 예약 (Reserved)
라이선스의 사용 ==> 전용 호스트 (Dedicated Host)  
Instance : 같이 쓰는 장비 / Host : 내 장비 (라이선스 가능)  
• 온디맨드 인스턴스 - 약정 없이 초당 사용한 만큼 비용 지불  
• 스팟 인스턴스 - 사용 안 하는 인스턴스를 경매 방식으로 구매하여 사용  
• 예약 인스턴스 - 1년 또는 3년 기간을 약정하여 인스턴스를 사용, 수요가 꾸준하고 예측가능한 경우에 유용  
• Saving Plan - 1년 또는 3년 기간의 일정 사용량을 약정하여 시간당 요금으로 인스턴스를 사용  
• 전용 호스트 - 물리적인 전용 서버를 할당 받아 사용하는 방식   
                          소켓당, 코어당 또는 VM 당으로 사용하는    소프트웨어 라이선스 사용 가능  
                          CPU 코어나 물리적 서버에 할당되는 라이선스를   기존에 보유한 경우에 적합  
• 전용 인스턴스 - 물리적인 전용 서버를 할당 받아 사용하는 방식  
                             전용 호스트에서 사용가능한 CPU 코어,   인스턴스 배치, 사용자 라이선스 사용 불가  


7. 데이터 마이그레이션 도구
데이터 마이그레이션 도구 : AWS Storage Gateway, AWS DataSync, AWS Transfer Family, AWS Snow Family, AWS Database Migration Service

Storage Gateway : 온라인 데이터백업용으로 나스처럼 지원되는 서비스  
DataSync : Storage GW 비슷하지만 파일만 지원, 데이터 카피 지원, 계속적인 복제 가능  
Transfer Family : FTP등의 파일 전송기술로 데이터를 전송할 수 있는 방식  
 
Data Sync : 데이터 전송에 초점이 맞춰져 있다.  
Storage Gateway는 전송되는 데이터에 엑세스하는 것에 초점이 맞춰져 있다.   
• EFS(Elastic File System)
- NFS프로토콜을 이용하는 리눅스 OS에서 사용하는 네트워크 파일 스토리지
- 여러 가용영역에 있는 수십~수백대의 EC2를 하나의 EFS연결 가능

• EBS(Elastic Block Store)
- 동일한 가용영역에 있는 1개의 EC2에만 연결 가능한 블록 스토리지
- 여러 개의 EBS 볼륨을 생성해서 EC2에 연결 가능 (1개의 EC2에 여러 개 EBS 연결 가능)
  즉, [볼륨:EC2=N:1] 관계

• Storage Gateway 
- 온프레미스 데이터 센터의 데이터와 AWS 클라우드의 스토리지를 연결하는 서비스(파일/볼륨/테이프 게이트웨이)
- 하이브리드 클라우드 스토리지로도 부름 (온프레미스 인프라 + 클라우드 인프라)

[참고] Amazon Redshift  
- 스토리지 서비스가 아니라 데이터 분석 서비스임
- 데이터 웨어하우스는 정보에 입각한 의사 결정을 내릴 수 있도록 분석 가능한 정보의 중앙 리포지토리

8. 고가용성  
   : Multi-AZ