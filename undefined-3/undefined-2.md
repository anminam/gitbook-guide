# 버블소트

## 구현

```javascript
const bubbleSort = () => {
    const arr = [5,2,4,1,3];
    print('최초');
    print(arr);

    const len = arr.length;
    for (let i=0; i < len; i++) {
        for (let j=0; j < len-1-i; j++) {
            if (arr[j] > arr[j+1]) {
                let t = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = t;
            }
        }
        print(`${i+1}번째 ${arr}`);
    }

    print('결과');
    print(arr);
}
```

## 결과

```javascript
최초
5,2,4,1,3
1번째 2,4,1,3,5
2번째 2,1,3,4,5
3번째 1,2,3,4,5
4번째 1,2,3,4,5
5번째 1,2,3,4,5
결과
1,2,3,4,5
```

