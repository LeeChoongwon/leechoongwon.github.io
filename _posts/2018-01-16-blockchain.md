---
layout: post
title: 블록체인 기술과 비트코인
categories:
  - Study
  - Technology
date: 2018-01-16 00:00:01 +09:00
comments: true
visible: 1
---

4차산업혁명을 선도할 기술 중 하나인 블록체인 기술과 비트코인에 대해 알아봅시다.

## 목차
{:.no_toc}

0. toc
{:toc}

<figure>
<img src="/assets/posts/20180116/101.png" width="600">
<figcaption align="middle">
</figcaption>
</figure>

블록체인 (영어: block chain)은 관리 대상 데이터를 '블록'이라고 하는 소규모 데이터들이 P2P방식을 기반으로 생성된 체인 형태의 연결고리 기반 분산 데이터 저장환경에 저장되어 누구도 임의로 수정될 수 없고 누구나 변경의 결과를 열람할 수 있는 분산컴퓨팅 기술 기반의 데이터 위변조 방지 기술이다.
[블록체인 - 위키백과, 우리 모두의 백과사전](https://ko.wikipedia.org/wiki/%EB%B8%94%EB%A1%9D%EC%B2%B4%EC%9D%B8)

> 당장 쉽게 이해하기 어렵다

## 블록체인
쉽게 말하면, 블록체인은 데이터 분산 처리 기술입니다.
블록체인 기술의 **응용 사례** 인 암호화폐(cryptocurrency) 를 예로 들어 보겠습니다.

기존 은행 업무나, 전자상거래에서는 거래장부를 은행이 단독으로 관리 저장하였습니다.
예를 들어 A가 B에게 100원을 송금하겠다고 하면, 그 연결 통로는 은행이 되며 은행이 단독으로 그 업무를 수행했습니다.
만약 해커가 그 내역을 변조하고 싶다면, 은행 한 군데만 해킹하면 되었습니다.


그러나 블록체인 기술은 블록체인 네트워크를 형성하고 있는 다수의 참여자들이 장부를 나누어 저장합니다.
같은 예로 A가 B에게 100원을 송금한다는 내역을 그 블록체인 네트워크에 참여하는 다수의 노드에 분산시켜 저장합니다.  그렇기 떄문에 해커가 그 정보를 빼돌리거나, 변조하고 싶더라고, 다수의 노드에 분산되어 있기 때문에, 해킹은 거의 불가능합니다.

### 특징
위에서 언급한 것처럼 분산하여 저장하기 때문에, 해킹이 어렵고,  모든것을 총괄하여 관리하는 책임자가 필요 없습니다.  네트워크의 모든 참여자가 관리자가 됩니다.

## 암호화폐
### 비트코인

<figure>
<img src="/assets/posts/20180116/102.png" width="600">
<figcaption align="middle">
</figcaption>
</figure>

비트코인은 암호화폐의 한 종류로, 블록체인 기술에 기반하여 생겨났습니다. <br />
지금까지의 화폐는 은행이 발행하고, 국가가 보증하였습니다. 그런데 블록체인 기술에 의하면, 은행은 필요 없고,  책임 관리자가 없기 때문에 암호화폐의 발행이  가능해졌습니다.  개인이 직접 `채굴`에 참여하고 발행할 수 있게 되었습니다.



### 채굴이란?
한때 비트코인 채굴기가 인기를 끌어, 그래픽카드를 구하기가 어려웠습니다. 집에서 채굴하다 전기값 폭탄을 맞은 사람도 있고, 대규모로 사업장을 운영하는 사람도 있습니다.
기존 화폐와 전혀 다른 시스템으로 채굴은 대부분의 사람들에게 생소한 행위입니다.

채굴 프로그램을 실행하는 채굴 컴퓨터는 거래 블록이 생성될 때마다, 수없이 많은 연산을 수행해야 하는 수학 문제를 풉니다. 그 문제를 해결하면 비트코인이 보상으로 주어집니다. 또, 두 비트코인 지갑 사이에서 거래가 이루어 질때, 거래 블록으로 참여하고 일정의 수수료를 받습니다.

<!-- ad -->

비트코인 채굴 보상은 4년마다 절반으로 줄어듭니다.
비트코인의 총 발행량은 21,000,000 BTC (2100만 비트코인) 이며,  2018년 1월 15일 기준 16,805,075 BTC 가 채굴 되었습니다. <br />
기하급수적으로 감소하기 때문에 해가 갈수록 채굴량은 감소하고 가치는 높아질 것으로 예상되고 있습니다.
소수점 8자리까지 분할할 수 있기 때문에 (사토시단위) 전부 발행 되더라도 가치 상승과 하락에 대응이 가능하도록 설계되었습니다.


### 가치
눈에 보이지도 않는 것이 무슨 화폐냐,  도대체 화폐로서의 기능을 수행할 수 있을까 많은사람들이 우려의 시선으로 바라보고 있습니다.
시장가격을 도저히 예측할 수 없을 정도로 수도없이 많이 상승과 하락을 반복하고,  투기의 대상으로 보는 사람들도 많습니다.
사실 단정 짓기는 어렵습니다.  내일 2배가 되어있을 수도 있는데 비트코인으로 무언가를 선뜻 구매하기는 힘들것 같습니다.

### 범죄 가능성
중앙체계가 없고, 익명성이 보장되는 거래로 인해 자금 세탁이나, 암시장에서 마약 등을 사고팔때 사용되고 있다.
해킹의 우려도 없을 수 없다. 실제로 암호화폐 거래소가 해킹당해 파산신청을 한 예도 있다.

## 미래
비트코인의 소스코드를 공개한 뒤, 개선에 개선을 한 암호화폐들의 등장도 블록체인 기술이 점점 발전하고 있음을 볼 수 있습니다.
블록체인 기술은 가까운 미래에 존재한다고 봅니다. 탈중앙 시스템의 높은 보안과 신뢰성이 앞으로의 기술 변화에 가져올 효과는 크다고 생각합니다.