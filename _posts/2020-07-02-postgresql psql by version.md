---
comments: true
title: PostgreSQL 버전별 psql 접근
key: 2020-07-02
picture_frame: shadow
tags:
  - PostgreSQL
---


# PostgreSQL 버전별 psql 접근

## 개요
 - postgreSQL의 버전별 호환성에 대한 테스트가 필요한 경우가 있다.
 - 물리적으로 하나로 구성된 서버에 여러 버전의 postgreSQL를 설치하는것이 서버 리소스관리나 테스트 환경에서 접근이 편리하다.
 - 각 버전별 포트를 달리하여 Connection 정보를 구분할 수 있음
 - 각 버전별 서비스를 구동할 수 있음

##  PostgreSQL Home directory
 - 일반적으로 postgreSQL의 Home Directory는 다음과 같음
	```
	/etc/postgesql
	```

## 여러버전이 존재하는 경우
 - postgresql은 home directory에 버전별로 directory 구조를 관리함
 - 예시는 다음과 같음
	```
	drwxr-xr-x   3 postgres postgres  4096 11월 19  2018 9.6/
	drwxr-xr-x   3 postgres postgres  4096  3월 18 09:14 10/
	drwxr-xr-x   3 postgres postgres  4096  1월 18 10:42 11/
	```
 - 각 버전 별로는 하위에 main directory가 존재하며 각 버전 별 환경설정 파일이 존재함

##  PostgreSQL 버전별 psql 접근 방법
 - 위 내용에서 postgreSQL의 디렉토리 구조를 설명한 것은 버전 별 postgreSQL 접근 방법이 postgreSQL의 디렉토리 구조와 연관이 있기 때문
 - 각 버전 별 psql 접근 방법은 다음과 같이 명령어를 수행 할 수 있음
	```
	psql --cluster 10/main
	psql --cluster 11/main
	psql --cluster 9.6/main
	```
 - psql 명령어 수행 시 환경변수에 정의된 postgreSQL 디렉토리를 참조하고 --cluster 명령어를 통해 실행하고자 하는 버전을 명시 할 수 있음