---
comments: true
title: VirtualBox 브릿지 어댑터 등록
key: 202007026
picture_frame: shadow
tags:
  - VirtualBox
---

# VirtualBox 브릿지 어댑터 등록

## 시작

 - 간혹 VirtualBox에서 Bridge Adapter를 사용하려고 하는 경우 아래와 같이 어댑터를 찾지 못하는 문제에 직면하게 된다.
 - 이와 관련하여VirtualBox 게스트 네트워크 드라이버 문제로서 네트워크 드라이버 설치 과정에 대해 설명한다.

<img src="https://github.com/huvso/study/blob/master/VirtualBox/03%20make%20bridge%20adapter/img/01.png?raw=true" align="center" title="make bridge adapter 01" alt="make bridge adapter 01"/>

******************

## VirtualBox 네트워크 드라이버 설치
<img src="https://github.com/huvso/study/blob/master/VirtualBox/03%20make%20bridge%20adapter/img/02_marked.png?raw=true" align="center" title="make bridge adapter 02" alt="make bridge adapter 02"/>
```
1. 제어판 이동(win+R -> control 입력)
2. 네트워크 및 공유 센터 클릭
```
******************

<img src="https://github.com/huvso/study/blob/master/VirtualBox/03%20make%20bridge%20adapter/img/03_marked.png?raw=true" align="center" title="make bridge adapter 03" alt="make bridge adapter 03"/>
```
1. 어댑터 설정 변경 클릭
```
******************

<img src="https://github.com/huvso/study/blob/master/VirtualBox/03%20make%20bridge%20adapter/img/05_marked.png?raw=true" align="center" title="make bridge adapter 05" alt="make bridge adapter 05"/>
```
1. VirtualBox Host-Only Ethernet Adapter 마우스 우측 클릭
2. 속성 클릭
```
******************

<img src="https://github.com/huvso/study/blob/master/VirtualBox/03%20make%20bridge%20adapter/img/06_marked.png?raw=true" align="center" title="make bridge adapter 06" alt="make bridge adapter 06"/>
```
1. 설치 클릭
```
******************

<img src="https://github.com/huvso/study/blob/master/VirtualBox/03%20make%20bridge%20adapter/img/07_marked.png?raw=true" align="center" title="make bridge adapter 07" alt="make bridge adapter 07"/>
```
1. 서비스 클릭
2. 추가 클릭
```
******************

<img src="https://github.com/huvso/study/blob/master/VirtualBox/03%20make%20bridge%20adapter/img/08_marked.png?raw=true" align="center" title="make bridge adapter 08" alt="make bridge adapter 08"/>
```
1. 디스크 있음 클릭
```
******************

<img src="https://github.com/huvso/study/blob/master/VirtualBox/03%20make%20bridge%20adapter/img/09_marked.png?raw=true" align="center" title="make bridge adapter 09" alt="make bridge adapter 09"/>
```
1. 찾아보기 클릭
```
******************

<img src="https://github.com/huvso/study/blob/master/VirtualBox/03%20make%20bridge%20adapter/img/10_marked.png?raw=true" align="center" title="make bridge adapter 10" alt="make bridge adapter 10"/>
```
1. "C:\Program Files\Oracle\VirtualBox\drivers\network\netlwf" 경로 이동
2. VBoxNetLwf.inf 클릭
3. 열기 클릭
```
******************

<img src="https://github.com/huvso/study/blob/master/VirtualBox/03%20make%20bridge%20adapter/img/11_marked.png?raw=true" align="center" title="make bridge adapter 11" alt="make bridge adapter 11"/>
```
1. 확인 클릭
```
******************

<img src="https://github.com/huvso/study/blob/master/VirtualBox/03%20make%20bridge%20adapter/img/12_marked.png?raw=true" align="center" title="make bridge adapter 12" alt="make bridge adapter 12"/>
```
1. 확인 클릭
```
******************

<img src="https://github.com/huvso/study/blob/master/VirtualBox/03%20make%20bridge%20adapter/img/13_marked.png?raw=true" align="center" title="make bridge adapter 13" alt="make bridge adapter 13"/>
```
1. VirtualBox NDIS6 Bridged Networking Driver 추가 확인
2. 확인 클릭
```
******************

<img src="https://github.com/huvso/study/blob/master/VirtualBox/03%20make%20bridge%20adapter/img/14_marked.png?raw=true" align="center" title="make bridge adapter 14" alt="make bridge adapter 14"/>
```
1. VirtualBox 가상머신 네트워크 브릿지 이름 확인
```
******************