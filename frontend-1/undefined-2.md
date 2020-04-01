# 최적화

##  변대리님과 함께하는 html css 최적화

1. doctype을 명시한다 doctype에 lang="ko"와 같이 lang을 명시한다.
2. script 태그를 문서 하단에 배치한다 bullet과 같은 디자인 아이콘은 css background로 사용한다
3. a href 더보기와 같은 버튼은 button 태그로 수정한다
4. css charset utf-8은 반드시 있어야됩니다 반드시 반드시 반드시
5. css import는 제거한다.
6. text-indent: -9999px 과 같이 퍼포먼스 저하를 유발하는 코드는 사용하지 않는다.

   피가되고 살이되는 명언이다

## 최적화 방법 3가지

### 바이트 수를 최소화

#### Minify, Compress, Cache

* html, css, JavaScript

#### Minimize use of render blocking resources\(css\)

*  미디어 쿼리 사용
*  인라인 CSS

#### Minimize use of parser blocking resource\(js\)

*  자바스크립트 실행보류
* async 속성을 스크립트 태그에 이용 

###  리소스 수 최소화

###  크리티컬 랜더 패스를 줄여라





## 아래는 정리 안된 상태입니다.

* **공백 제거**
* **주석제거**
* **인라인화**
* **압축**
* **브라우저 케싱**
* **링크테그에서 미디어속성으로 css 랜더블로킹 최소화**
* **리소스 수를 줄여**





\*\*\*\*

