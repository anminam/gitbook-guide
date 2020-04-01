---
description: Cross Domain
---

# CORS

## 서버 해결방법

> 해당 방법은 node.js 로 이루어져 있습니다.

### **1. Access-Control-Allow-Origin response 헤더를 추가**

```javascript
app.get('/data', (req, res) => {
    // 모든 사이트 허용
    res.header("Access-Control-Allow-Origin", "*");
    
    // 특정 메소드 허용
    // "Access-Control-Allow-Methods", "POST, GET, OPTIONS, DELETE");
    res.send(data);
});
```

### 2. **미들웨어 CORS\(node.js\) 추가**

```bash
$ npm install --save cors

// or

$ yarn add cors
```

```bash

```

## 클라이언트 해결방법 -\(사실 해결못함\)

### JSONP

* 특정 사이트의 api를 요청을 할때 js, css 등 리소스 파일들은 정책에 위배되지 않고 다운로드가 가능하다. 서버에서 리소스 파일들을 읽고 그 결과를 json으로 바꿔주는 하나의 편법이다.
* get 방식만 가능하다 

## 리엑트에서

* [https://create-react-app.dev/docs/proxying-api-requests-in-development](https://create-react-app.dev/docs/proxying-api-requests-in-development/)





## 참고사이트

* [https://velog.io/@jmkim87/%EC%A7%80%EA%B8%8B%EC%A7%80%EA%B8%8B%ED%95%9C-CORS-%ED%8C%8C%ED%97%A4%EC%B3%90%EB%B3%B4%EC%9E%90](https://create-react-app.dev/docs/proxying-api-requests-in-development/)

