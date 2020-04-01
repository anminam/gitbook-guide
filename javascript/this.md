---
description: '''this''에 대해서 알아보자'
---

# this

> 콘솔에서 단순히 this 를 호출하는 경우 해당 this 는 window 이다

```javascript
this; // Window {}

// 웹 브라우저에서는 window 객체가 전역 객체
console.log(this === window); // true
```

> 함수 f1 를 호출 할 경우 해당 this는 window 를 가르킨다

```javascript
function f1() {
    return this;
};
f1() === window; // true 
```

> 엄격모드는 다르다, this 값은 실행 문맥에 진입하며 설정되는 값을 유지하므로

```javascript
function f2(){
  "use strict"; // 엄격 모드 참고
  return this;
}

f2() === undefined; // true
```

> 실행문맥을 넘기고싶으면 **call\(\),** **apply\(\)**를 사용.
>
> 매개변수가 없을경우

```javascript
// call()이나 apply()의 첫 번째 매개변수로 객체를 제공하면 this가 그 객체에 묶임
var obj = {a: 'Custom'};

// 전역 객체에 속성 지정
var a = 'Global';

function whatsThis() {
  return this.a;  // 함수 호출 방식에 따라 값이 달라짐
}

whatsThis();          // 'Global'
whatsThis.call(obj);  // 'Custom'
whatsThis.apply(obj); // 'Custom'
```



> 문맥을 넘기고싶으면 **call\(obj, a, b\),** **apply\(obj, \[a, b\]\)**를 사용.
>
> 매개변수가 있을경우

```javascript
function add(c, d) {
  return this.a + this.b + c + d;
}

var o = {a: 1, b: 3};

// 첫 번째 매개변수는 this를 묶을 객체
// 이어지는 인수들은 함수 호출에 사용할 매개변수
add.call(o, 5, 7); // 16

// 첫 번째 매개변수는 this를 묶을 객체
// 두 번째 매개변수는 배열,
// 각 요소를 함수 호출에 사용
add.apply(o, [10, 20]); // 34
```

## bind

> bind 할 경우 this는 원본 함수를 가진 새로운 함수를 생성
>
> 새로운 함수는 this의 호출방식과 상관없이 영구적으로 처음 bind\(\) 한 첫번째 매개변수로 고정

```javascript
function f() {
  return this.a;
}

var g = f.bind({a: 'azerty'});
console.log(g()); // azerty

var h = g.bind({a: 'yoo'}); // bind는 한 번만 사용 가능!
console.log(h()); // azerty

var o = {a: 37, f: f, g: g, h: h};
console.log(o.a, o.f(), o.g(), o.h()); // 37,37, azerty, azerty
```

## 화살표함수

> 화살표함수에서 this는 자신을 감싼 정적범위\(lexical context\)

```javascript
var globalObject = this;
var foo = (() => this);
console.log(foo() === globalObject); // true
```

## 

## 기타정리

> obj 의 함수 a 를 호출함으로 this는 자신을 호출한 obj 를 가르킨다

```javascript
var obj = {
  a: function() {  
    console.log(this);
  },
};
obj.a(); // obj
```

> obj.a를 함수 a2 에 할당하고, 함수 a2 를 호출하면 해당 함수호출은 window서 호출했기 때문에 해당 this는 window 를 가르킨다

```javascript
var a2 = obj.a;
a2(); // Window {}
```

```javascript
var obj = { a: 'b' };
function c() {
  console.log(this);
}
c(); // Window {}
c.bind(obj).call(); // obj
c.call(obj); // obj 
c.apply(obj); // obj
```

```javascript
function Person (name, age) {
    this.name = name;
    this.age = age;
}

Person.prototype.sayHi = function () {
    console.log(this.name, this.age);
}
```

```javascript
var hero = new Person('Anminam', 34); // Person {name: "Anminam", age: 34}
hero.sayHi(); // Anminam 34
```

```javascript
Person('Anminam', 34);
console.log(window.name, window.age); // Anminam 34
```

```javascript
document.body.onclick = function() {
  console.log(this); // <body>
}
```

## 차이점  

```javascript
// ES5
function callFunc() {
    return {
        foo : 555,
        bar : function() {
            console.log(this.foo);
        }
    }
}

callFunc.call({foo:777}).bar(); // 555

// ES6
function callFunc() {
    return {
        foo : 555,
        bar : () => {
            console.log(this.foo);
        }
    }
}
callFunc.call({foo:777}).bar(); // 777
```

##  참고사이트

* [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/this](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/this)
* [https://www.zerocho.com/category/JavaScript/post/5b0645cc7e3e36001bf676eb](https://www.zerocho.com/category/JavaScript/post/5b0645cc7e3e36001bf676eb)

