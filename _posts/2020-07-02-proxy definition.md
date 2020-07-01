---
comments: true
title: Proxy란?
key: 202007024
picture_frame: shadow
tags:
  - [Infrastructure, Proxy]
---
# What is Proxy

## 프록시 서버(Proxy Server)
### What is Proxy Server
 - 사전적인 의미로는 '대리인'
 - 클라이언트가 자신을 통해서 다른 네트워크 서비스에 간접적으로 접속할 수 있게 해 주는 컴퓨터나 응용 프로그램
 - 서버와 클라이언트 사이에서 중계기로서 대리로 통신을 수행하는 기능을 가리켜 **'프록시'**, 그 중계 기능을 하는 것을 **'프록시 서버'** 라고 부름
 
### Advantage of Proxy Server
 - 프록시 서버에 요청된 내용들을 캐시에 저장 후, 캐시 안에 있는 정보를 이용함으로써 불필요하게 외부와의 연결을 하지 않아 전송 시간을 절약 할 수 있음
 - 외부와의 트래픽을 줄이게 됨으로써 네트워크 병목 현상을 방지하는 효과도 얻을 수 있음

### Purpose of Proxy Server
 - 캐시를 사용하여 리소스로의 접근 속도 향상
 - 원하지 않는 사이트 차단
 - 인터넷 이용률 기록, 검사
 - 악의적인 의도로 바이러스, 악성 루머 전파 또는, 다른 정보들을 빼낼 목적
 - IP 추적을 방지
 - In/Out 콘텐츠 검사
 - 우회
- - -

&nbsp;
&nbsp;
&nbsp;
  
## 투명 프록시(Transparent Proxy)
### Definition
 - 투명 프록시는 사용자와 컨텐츠 프로바이더 사이에 존재하는 중개 시스템임
 - 사용자가 웹 서버에 요청을 하면 투명 프록시는 캐싱, 리디렉션 및 인증을 포함한 요청을 가로챔
 <img src="https://github.com/huvso/study/blob/master/proxy%20Server/img/01.png?raw=true" align="center" title="proxy 01" alt="proxy 01"></img>

### Overview
 - 웹 프록시는 요청을 가로 채고, 필요한 경우 요청을 수정 한 다음 요청을 처리하거나 목적지로 전달함으로써 작동함
 - 서비스 공급자는 프록시를 사용하여 사용자가 서비스에 연결하는 방식을 형성하고 최적화 할 수 있음
 - 네트워크 공급자가 사용자 또는 직원이 외부 리소스에 액세스하는 방식에 영향을 줄 수 있음
 - 일반적으로 프록시는 사용자의 응용 프로그램 또는 네트워크 설정을 구성하여 액세스함
 - 투명 프록시를 사용하면 프록시는 대상으로 향하는 패킷을 가로 채서 요청을 가로 챌 수 있으므로 요청이 대상 자체에서 처리되는 것처럼 보임
 - 서비스 제공 업체는 사용자 컴퓨터를 재구성하지 않고도 프록시를 구현할 수 있음

### How Transparent Proxies work
 - 투명 프록시는 사용자와 웹서비스 사이에서 중개자로서 활동한다
 - 사용자가 서비스에 연결 할 때 투명 프록시는 서비스 제공업체에 도착하기 전에 요청을 가로챈다
 - 투명 프록시는 사용자들이 이것을 알지 못하기 때문에 투명하게 간주된다
 - 반면에 서비스를 호스팅하는 서버는 프록시 트래픽이 사용자로 부터 직접적인게 아닌 프록시로 부터 오는 것을 인식한다
#### Use of Transparent Proxies
 - 투명 프록시는 다양하다
 - 다음 목록에는 투명 프록시가 사용되는 일반적인 예이다.
 - **Proxy cache** : Proxy cache는 서버에 저장된 데이터의 복사본을 만들고 캐시 된 콘텐츠를 사용자에게 제공한다. 이렇게 하면 프록시가 서비스 자체 대신 콘텐츠를 제공하도록 함으로써 웹 서비스의 부담을 줄일 수 있다
 - **Filtering proxy** : Filtering proxy는 특정 웹 사이트 또는 웹 서비스에 대한 액세스를 차단한다. 이는 일반적으로 조직에서 관련이 없거나 조직에 지장이 없는 리소스에 사용자가 액세스하지 못하도록하기 위해 조직에서 구현한다.
 - **Gateway proxy** : Gateway proxy는 네트워크 트래픽을 수정하거나 차단한다. 공용 Wi-Fi를 제공하는 위치는 종종 사용자가 서비스를 사용하기 전에 계약을 등록하거나 수락해야하는 게이트웨이를 구현한다.

### Example of a Transparent Proxy
 - 스타 벅스 커피 하우스 사용자는 상점의 Wi-Fi 네트워크에 연결하려고 한다. 사용자가 웹 브라우저를 열면 모든 네트워크 통신을 관리하는 프록시 서버에 연결된다. 이것은 새로운 사용자이므로 프록시는 사용자에게 특정 이용 약관에 동의하도록 요청하는 웹 페이지를 브라우저에 표시한다. 사용자가 수락하면 프록시는 사용자의 트래픽을 실제 대상으로 라우팅한다.
 - MaxCDN과 같은 콘텐츠 전달 네트워크는 대규모로 투명 프록시의 한 형태이다. CDN은 소스 시스템을 공개하거나 수정하지 않고도 캐싱, 중복성 및 속도 향상을 제공한다. 사용자는 서비스 제공 업체에 직접 연결한다고 생각하지만 모든 요청은 CDN에서 처리한다. 이것이 Google, Facebook 및 Twitter와 같은 서비스가 최소한의 중단 시간으로 수백만 건의 요청을 처리하는 방법이다.

### Benefits of Transparent proxy
투명 프록시는 사용자의 브라우징 경험에서 기능 및 feature들을 추가하는 괜찮은 방법이다.
 - **기업**은 들어오는 요청을 라우팅 및 수정하여 고객이 서비스와 상호 작용하는 방식을보다 효과적으로 제어 할 수 있다.
 - **사용자**는 연결이 프록시를 통해 원활하고 보이지 않게 전달되므로 서비스 공급자와 구성을 유지하면서 웹 서비스와보다 쉽게 상호 작용한다.
- - -
 &nbsp;
 &nbsp;
 &nbsp;


## Forward Proxy
### Definition
 클라이언트가 웹 서버에 접근 하려고 할 때 클라이언트의 요청이 웹서버에게 직접 전송되는 것이 아니고 중간에 Proxy 서버에게 전달되어 Proxy 서버는 그 요청을 웹 서버에게 전달하여 응답을 받아 오는 방식
 
### Use
 - Content Filtering
 - e-mail security
 - NAT ing
 - Compliance Reporting
- - -
 &nbsp;
 &nbsp;
 &nbsp;


## Reverse Proxy
### Definition
 클라이언트는 웹 서버의 주소가 아닌 Reverse Proxy로 설정된 주소로 요청을 하게 되고, Proxy 서버가 받아서 그 뒷단에 있는 웹 서버에게 다시 요청을 하는 방식으로 클라이언트는 진짜 웹 서버의 정보를 알 수가 없다
 
### Use
- Application Delivery including
- Load Balancing (TCP Multiplexing)
- SSL Offload/Acceleration (SSL Multiplexing)
- Caching
- Compression
- Content Switching/Redirection
- Application Firewall
- Server Obfuscation
- Authentication
- Single Sign On
- - -
 &nbsp;
 &nbsp;
 &nbsp;


## 참고 URL
 - https://www.tecmint.com/install-squid-in-ubuntu/
 - https://www.maxcdn.com/one/visual-glossary/transparent-proxy/
 - https://www.clien.net/service/board/lecture/11500797