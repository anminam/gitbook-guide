# 용어사전

## Polyfill - 폴리필

* **특정 기능이 지원되지 않는 브라우저**를 위해 사용할 수 있는 **코드 조각**이나 **플러그인**을 말한다.
* HTML5 및 CSS3와 **오래된 브라우저 사이의 간격을 메꾸는 역할**을 담당한다.

## 실행 컨텍스트\(Execution Context\)

**실행 가능한 코드를 형상화하고 구분하는 추상적인 개념**

### 실행 컨텍스트의 3가지 객체

* **Variable Object - VO**
* **Scope Chain - SC**
* **thisValue - this**

### Variable Object \(VO / 변수객체\) <a id="21-variable-object-vo--&#xBCC0;&#xC218;&#xAC1D;&#xCCB4;"></a>

* 변수
* 매개변수\(parameter\)와 인수 정보\(arguments\)
* 함수 선언\(함수 표현식은 제외\)

전역 컨텍스트의 경우Variable Object는 유일하며 최상위에 위치하고 모든 전역 변수, 전역 함수 등을 포함하는 **전역 객체\(Global Object / GO\)**를 가리킨다. 전역 객체는 전역에 선언된 전역 변수와 전역 함수를 프로퍼티로 소유한다.

함수 컨텍스트의 경우Variable Object는 **Activation Object\(AO / 활성 객체\)**를 가리키며 매개변수와 인수들의 정보를 배열의 형태로 담고 있는 객체인 [arguments object](https://poiemaweb.com/js-function#61-arguments-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)가 추가된다.

