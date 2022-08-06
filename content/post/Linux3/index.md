---
title: Linux공부 제 3장
description: Linux(Ubuntu) 명령어 정리
slug: start-Linux3
date: 2022-07-20
image: 
categories:
    - Linux
tags:
    - 리눅스공부
---

---

## Linux 명령어 정리


### 파일 관련 명령어

#### 빈 파일 생성
```shell
touch [ 파일명 ]
```

#### 파일 삭제
```shell
rm [ 파일명 ]
```

#### 파일 복사
```shell
cp [파일경로 및 파일이름] [원하는 경로 및 파일이름]
```

#### 파일 이동 (이름 변경시에도 사용)
```shell
mv [파일경로 및 파일이름] [원하는 경로 및 파일이름]
mv [원래 파일 이름] [원하는 파일 이름]
```

#### 파일 생성 및 기존 파일 수정(nano Editor)
```shell
nano [파일명]
```

#### 파일 내용 보기
```shell
cat [파일명]
```

#### 파일 위치 검색
```shell
locate *.[확장자명] : [확장자명]을 가진 파일 찾기 - 디렉토리가 아닌 데이터베이스에서 찾는다.
find . *.[확장자명] : [확장자명]을 가진 파일 찾기 - 디렉토리에서 찾는다.
whereis ls : 실행파일 위치 찾기
whereis rm : 실행파일 위치 찾기
```

#### 현재 경로 확인
```shell
pwd
```
 
#### 명령창 내용 삭제 
```shell
clear
```

#### 명령어 도움말 확인
```shell
[명령어] --help
man [명령어] :/[찾고싶은단어] 까지 옵션을 사용해서 특정 단어 찾기 가능, 그 상태를 유지한 상태로 n을 누르면 n이 들어간 단어 찾기 실행
```
### 패키지 매니저

#### 패키지 목록 업데이트
```shell
apt-get update
```

#### 패키지 찾기
```shell
apt-cache search [패키지명]
```

#### 패키지 설치
```shell
apt-get install [패키지명]
```

#### 패키지 업그레이드
```shell
apt-get upgrade : 패키지 목록에 있는 모든 패키지 업데이트
apt-get upgrade [패키지명] : 특정 [패키지명]만 업데이트
```

#### 패키지 삭제
```shell
apt-get remove [패키지명] : 특정 [패키지명] 삭제
```

### 다운로드

#### 파일 다운로드 (wget 사용)
```shell
wget -0 [저장할 파일명] [다운로드 url]
```

[//]: # (#### )

[//]: # (```shell)

[//]: # ()
[//]: # (```)
