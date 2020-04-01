---
description: 개인적인 생각...
---

# Loadmap

## 읽기전에..

*  코드 블럭이 예시로 있는경우 숫자를 카운트 하는 예제로 간단히 넣음

## Class Component

*  클래스로 이루어진 컴포넌트 만들기 연습

## Function Component

*  함수로 이루어진 컴포넌트 만들기 연습

## prop-types

* propTypes 연습
* defaultProps 연습

## Hook

* useState
* useEffect
* useState 와 useEffect를 이용한 필요한 use함수 만들기

## Router

*  라우팅, 라우팅 안에 라우팅 연습



## 이하 Redux

## ActionTypes

* 변수이름을 동사로 쓰지말라고 한거같은데.. 명사형으로쓰면 되는지 구로 만들면 되는지 ... 추후 다시 정리하자

```javascript
export const INCREMENT = 'INCREMENT';
export const DECREMENT = 'DECREMENT';
export const SET_COLOR = 'SET_COLOR';
```

## Action

```javascript
import { INCREMENT, DECREMENT, SET_COLOR} from "./ActionTypes";

export const increment = () => {
    return {
        type: INCREMENT
    }
}
export const decrement = () => {
    return {
        type: DECREMENT
    }
}
export const setColor = (color) => {
    return {
        type: SET_COLOR,
        color
    }
}

```

## Reducer

```javascript
import * as types from "../actions/ActionTypes";

const counter = (state = initialState, action) => {
    switch(action.type) {
        case types.INCREMENT:
            return {
                ...state
                number: state.number + 1
            }
        case types.DECREMENT:
            return {
                ...state
                number: state.number - 1
            }
        case types.SET_COLOR:
            return {
                ...state
                color: action.color
            }
        default:
            return {
            }
    
}
```

## combineReducers

* 합치기

## Store

*  단순 리듀서 받는 스토어
*  미들웨어 포함한 스토어는... 후순위로....

## Immutable

* Map 
* List
* set
* get
* update  

```javascript
// 어떤 배열의 인덱스에 'value'값을 더
return state.update(
    action.index,
    item => item.set('value', item.get('value') + 1
)
```









