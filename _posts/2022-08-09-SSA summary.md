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