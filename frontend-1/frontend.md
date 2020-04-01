---
description: 측정해보고 개선해라
---

# 기본개념

##  크리티컬 랜더링 패스 

* 브라우저가 html, css, javascript  화면에 실제 픽셀로 변화하는 단계
* 이 단계를  최적화하여 페이지를 빠르게 렌더링할 수 있다 .

{% hint style="info" %}
DOM -&gt; \(&lt;- JavaScript -&gt; \) -&gt; CSSOM -&gt; Render Tree -&gt; Layout -&gt; Paint
{% endhint %}

### HTML 을 DOM으로 변환 

* Characters - 단순 문자열을 받음 \(html\)
* Tokens - html, div, span 등등 을 토큰으로 변환
  * 해당과정을 Tokenizer 라고 함
* Nodes - 파서가 토큰들을 노드로 트리로 만듬 
* DOM -  위 과정으로  완성한것을 Document Object Model 이라 칭함 



### CSS를 CSSOM으로 변환 

* Characters - 단순 문자열을 받음 \(css\)
* Tokens - 토큰 확인작업
* Nodes - 파서가 토큰들을 노드로 트리로 만듬 
* DOM -  위 과정으로  완성한것을 Document Object Model 이라 칭함

{% hint style="danger" %}
브라우저 모든 CSS를 받고 처리할 때까지  페이지 렌더링을 차단한다. 
{% endhint %}

### Render Tree

* Dom 과 cssom 으로 랜더트리를 생성

### Layout

* 브라우저의 view port 안에서 노드의 위치와 크기를 계산하여 렌더트리에 반영

### **Paint**

* 레이아웃에서 계산된 결과값을 화면에 실제 픽셀로 변환



###  브라우저 랜더링 과정

{% hint style="info" %}
파싱 &gt; 스타일 &gt; 레이아웃 &gt; 페인트 &gt; 렌더
{% endhint %}

1.  파싱
   1. 다운받은 html을 파싱해서 **dom을 생성 후 트리 구축**
   2. 추가 리소스 요청 및 다운로드
   3. **cssom 을 생성 후 트리 구축**
2. **스타일**
   1. dom, cssom을 매칭해서 **렌더트리에 반영**
3. 레이아웃
   1. 브라우저의 view port 안에서 노드의 위치와 크기를 계산하여 **렌더트리에 반영** 
4. 페인트
   1.  **레이아웃에서 계산된 결과값을 화면에 실제 픽셀로 변환**
   2.  **위치와 상관없는 css속성들이 결정됨**
5. **렌더**
   1. **페인트 된 레이어들을 합쳐 업데이트**



\*\*\*\*

\*\*\*\*

\*\*\*\*

##  **참고사이트**

* \*\*\*\*[**https://youtu.be/mFiyWrwyV9s**](https://youtu.be/mFiyWrwyV9s)\*\*\*\*

\*\*\*\*

### 

