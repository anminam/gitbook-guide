# 비동기



####  일반적인 함수 사용

```javascript
<script type="text/javascript">
    window.onload = (e) => {
        const rootDOM = document.querySelector('#root');
        rootDOM.innerHTML = rootDOM.innerHTML + '윈도우로드다냥';
    }
</script>
```

## Callback

#### 비동기 이벤트가 많아질수록 callback 지옥에 빠지게 된다.

```javascript
<script type="text/javascript">
    window.onload = (e) => {
        const rootDOM = document.querySelector('#root');
        // div 를 추가해 주는 함수
        const print = (str) => {
            rootDOM.innerHTML = `${rootDOM.innerHTML}<div>${str}</div>`;
        }

        print('윈도우로드다냥');
        let num = 1;
        setTimeout(() => {
            print(`${num++} 번째 다냥`);
            setTimeout(() => {
                print(`${num++} 번째 다냥`);
                setTimeout(() => {
                    print(`${num++} 번째 다냥`);
                    setTimeout(() => {
                        print(`${num++} 번째 다냥`);
                        setTimeout(() => {
                            print(`${num++} 번째 다냥`);
                        }, 1000);
                    }, 1000);
                }, 1000);
            }, 1000);
        }, 1000)
    }
</script>
```

## Promise

```javascript
<script type="text/javascript">
    window.onload = (e) => {
        const rootDOM = document.querySelector('#root');
        const print = (str) => {
            rootDOM.innerHTML = `${rootDOM.innerHTML}<div>${str}</div>`;
        }
    
        let num = 1;
        const f1 = () => {
            return new Promise((resolve) => {
                setTimeout(()=> {
                    print(`${num++} 번째 다냥`);
                    resolve();
                },1000);
            }).then(() => {
                return new Promise((resolve) => {
                    setTimeout(()=> {
                        print(`${num++} 번째 다냥`);
                        resolve();
                    },1000);
                })
            }).then(() => {
                return new Promise((resolve) => {
                    setTimeout(()=> {
                        print(`${num++} 번째 다냥`);
                        resolve();
                    },1000);
                })
            }).then(() => {
                return new Promise((resolve) => {
                    setTimeout(()=> {
                        print(`${num++} 번째 다냥`);
                        resolve();
                    },1000);
                })
            }).then(() => {
                return new Promise((resolve) => {
                    setTimeout(()=> {
                        print(`${num++} 번째 다냥`);
                        resolve();
                    },1000);
                })
            })
        }
        // 실행
        f1();
    }
</script>
```

#### 위 코드를 축약하자면 아래와 같은 코드가 완성된다.  위코드와 아래의 코드의 결과는 같다.

```javascript
<script type="text/javascript">
    window.onload = (e) => {
        const rootDOM = document.querySelector('#root');
        const print = (str) => {
            rootDOM.innerHTML = `${rootDOM.innerHTML}<div>${str}</div>`;
        }

        let num = 1;
        const f1 = () => new Promise((resolve) => {
            setTimeout(()=> {
                print(`${num++} 번째 다냥`);
                resolve();
            },1000);
        });

        // 실행
        f1().then(f1).then(f1).then(f1).then(f1);
    }
</script>
```

> 아래와 같이 함수를 만들면 실행할때 눈으로 보기 편하다.

```javascript
<script type="text/javascript">
    window.onload = (e) => {
        const rootDOM = document.querySelector('#root');
        const print = (str) => {
            rootDOM.innerHTML = `${rootDOM.innerHTML}<div>${str}</div>`;
        }

        const eatLunch = () => new Promise((resolve) => {
            setTimeout(() => {
                print('밥먹는다.');
                resolve();
            }, 1000);
        });
        const drinkCoffee = () => new Promise((resolve) => {
            setTimeout(() => {
                print('커피를 마신다.');
                resolve();
            }, 1000);
        });
        const goToBed = () => new Promise((resolve) => {
            setTimeout(() => {
                print('잔다.');
                resolve();
            }, 1000);
        });

        // 실행
        eatLunch()                // 밥먹는다
            .then(drinkCoffee)    // 그리고나서 커피를마신다
            .then(goToBed);        // 그리고나서 잔다
    }
</script>
```

## async & await

> await 는 반드시 async 함수 안에서 사용해야 한다.

```javascript
<script type="text/javascript">
    window.onload = (e) => {
        const rootDOM = document.querySelector('#root');
        const print = (str) => {
            rootDOM.innerHTML = `${rootDOM.innerHTML}<div>${str}</div>`;
        }

        let num = 1;
        const f1 = () => new Promise((resolve) => {
            setTimeout(()=> {
                print(`${num++} 번째 다냥`);
                resolve();
            },1000);
        });
        // start 함수에 async 키워드를 붙인다
        const start = async () => {
            await f1();        // 각각의 호출할 Promise 타입의 함수를 호출할때 await를 붙인다.
            print('기다린다');
            await f1();
            print('기다린다');
            await f1();
            print('기다린다');
            await f1();
            print('기다린다');
            await f1();
            print('기다린다');
            await f1();
        }

        start();
    }
</script>
```

##  참고사이트

* [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global\_Objects/Promise](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Promise)
* [http://junil-hwang.com/blog/javascript-promise-async-await/](http://junil-hwang.com/blog/javascript-promise-async-await/)

