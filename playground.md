# PlayGround



```markup
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <div id="root">
    </div>
    
    <script src="https://npmcdn.com/axios/dist/axios.min.js"></script>
    <script src="./index.js"></script>
</body>
</html>
```

```javascript
window.onload = (e) => {
    init();
}


const init = () => {
    axios.get('https://api.openweathermap.org/data/2.5/weather?q=London&appid=eb7343bdb9fa9d75ca84237f0c496425')
        .then(data => {
            if(!data) return;
            const {data:{name}} = data;
            print(name);
        });
}

const print = (text) => {
    const rootDOM = document.querySelector('#root');

    rootDOM.innerHTML = rootDOM.innerHTML + `<div>${text}</div>`;
}
```

