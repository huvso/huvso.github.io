---
comments: true
title: VirtualBox 새 머신 만들기
key: 202007012
picture_frame: shadow
tags:
  - VirtualBox
---

# VirtualBox 새 머신 만들기

## 새 머신 생성하기
### 1. 머신 생성 마법사 실행
<img src="https://github.com/huvso/study/blob/master/VirtualBox/01%20make%20virtual%20image/img/01_marked.png?raw=true" align="center" title="make vimg 01" alt="make vimg 01">
```
1. 처음 나오는 화면에서 새로 만들기(N) 클릭
```

```
! 첫 화면과 다른 화면이 보인다면 다음과 같이 첫 화면으로 이동 할 수 있음
```
<img src="https://github.com/huvso/study/blob/master/VirtualBox/01%20make%20virtual%20image/img/01_01_marked.png?raw=true" align="center" title="make vimg 01_01" alt="make vimg 01_01">
******************

### 2. 이름 및 운영 체제 정의
<img src="https://github.com/huvso/study/blob/master/VirtualBox/01%20make%20virtual%20image/img/02_marked.png?raw=true" align="center" title="make vimg 02" alt="make vimg 02">

```
1. 각 내용에 지정하고자 하는 내용을 입력함
  - 이름: 가상 머신의 식별을 위한 이름
  - 머신 폴더: 가상 머신에 관련된 정보들이 저장될 경로(해당 폴더안에 이름 별로 폴더가 생성됨)
  - 종류: 설치할 OS 계열
  - 버전: 설치할 OS의 상세 종류 (버전, OS 상세 계열, bit 수)

2. 다음(N) 클릭
```
******************

### 3. 메모리 크기 정의
<img src="https://github.com/huvso/study/blob/master/VirtualBox/01%20make%20virtual%20image/img/03_marked.png?raw=true" align="center" title="make vimg 03" alt="make vimg 03">

```
1. 생성 하고자 하는 메모리 크기를 정의
  - 슬라이더 또는 박스에 숫자로 기입 할 수 있음

2. 다음(N) 클릭
```
******************

### 4. 하드 디스크 정의
<img src="https://github.com/huvso/study/blob/master/VirtualBox/01%20make%20virtual%20image/img/04_marked.png?raw=true" align="center" title="make vimg 04" alt="make vimg 04">

```
1. 지금 새 가상 하드 디스크 만들기(C) 라디오버튼 선택
  - 가상 하드디스크를 추가하지 않음: 가상 머신 생성 시 디스크를 만들지 않음
  - 지금 새 가상 하드 디스크 만들기: 가상 머신 생성 시 새로운 가상 디스크를 만듦
  - 기존 가상 하드 디스크 파일 사용: 기존에 생성된 가상 디스크를 해당 가상 머신에서 사용

2. 만들기(N) 클릭
```
******************

### 5. 하드 디스크 파일 종류 정의
<img src="https://github.com/huvso/study/blob/master/VirtualBox/01%20make%20virtual%20image/img/05_marked.png?raw=true" align="center" title="make vimg 05" alt="make vimg 05">

```
1. VDI(VirtualBox Disk Image) 라디오버튼 선택
  - VDI(VirtualBox Disk Image): VirtualBox에서만 사용이 가능한 형태
  - VHD(Virtual Hard Disk): VirtualBox(Oracle), Hyper-V(MS), Xen(Citrix)에서 사용이 가능한 형태
  - VMDK(Virtual Machine Disk): VirtualBox(Oracle), VMWare(MS)에서 사용이 가능한 형태

2. 다음(N) 클릭
```
******************

### 6. 파일 위치 및 크기 종류 정의
<img src="https://github.com/huvso/study/blob/master/VirtualBox/01%20make%20virtual%20image/img/06_marked.png?raw=true" align="center" title="make vimg 06" alt="make vimg 06">

```
1. 파일 위치는 default로 정의하는 것이 좋음
2. 새 가상 하드 디스크 크기 정의
  - 슬라이더 또는 박스에 숫자로 기입 할 수 있음
2. 만들기 클릭
```
******************

### 7. 가상 하드 디스크 만들기 Process 창
<img src="https://github.com/huvso/study/blob/master/VirtualBox/01%20make%20virtual%20image/img/07.png?raw=true" align="center" title="make vimg 07" alt="make vimg 07">
```
1. 가상 하드 디스크 구성 중인 화면으로 가상 하드 디스크의 크기에 따라 생성 시간에 차이가 있음
```
******************

### 8. 새 가상 머신 만들기 완료
<img src="https://github.com/huvso/study/blob/master/VirtualBox/01%20make%20virtual%20image/img/08_marked.png?raw=true" align="center" title="make vimg 08" alt="make vimg 08">
```
좌측 신규 가상 머신이 제대로 생성 되었는지 확인
```