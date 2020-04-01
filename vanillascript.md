# VanillaScript

##  참고사이트

###  클래스를 잘 이용한 사이트

* [https://blog.jeremylikness.com/blog/2019-04-09\_vanilla.jsgetting-started](https://blog.jeremylikness.com/blog/2019-04-09_vanilla.jsgetting-started/)

##  셀렉터

```javascript
// 그냥 쿼리 셀렉터 쓰자 
const item = document.querySelector('.아이템');
```

##  이벤트

```javascript
// 이벤트
let 엘리먼트 = document.querySelector('#아이디');
const onClick = (event) => {
    console.log('클릭 됨');
}

엘리먼트.addEventListener('click', onClick);
```

##  초기화

```markup
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" type="text/css" href="./style.css">

    <title>Document</title>
</head>
<body>
    <div id="app"></div>
    <script type="module" src="./app.js"></script>
</body>
</html>
```

##  통신

```javascript
fetch('https://jsonplaceholder.typicode.com/posts').then((res) => {
	// 성공
	console.log('성공', res);
}).catch(function (err) {
	// 실패
	console.warn('실패', err);
});
```

```javascript
const 통신 = async () => {
    await fetch('https://jsonplaceholder.typicode.com/posts').then((response) => {
        // 성공
        console.log('성공', response);
        return true;
    }).catch(function (err) {
        // 실패
        console.warn('실패', err);
        return false;
    });

}

const 로직시작 = async () => {
    await 통신();

    console.log('이것은 제일 나중에 나와야함')
}

로직시작();
```

```javascript
const getUserAsync = async (name) => {
  let response = await fetch(`https://api.github.com/users/${name}`);
  let data = await response.json()
  return data;
}

getUserAsync('anminam')
  .then(data => console.log(data)); 
```



