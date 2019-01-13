---
title: redux
tags:
  - 개발
  - redux
date: 2018-03-25 11:11:11
---
# [](#redux-간단개요 "redux 간단개요")redux 간단개요

### [](#학습목표 "학습목표")학습목표

리액트 필터링 기능 App.js예제에서 동작 원리를 알아본다.  
  

* * *

Flux 패턴은 라이브러리가 아닌 하나의 설계 방법론일 뿐이다.

parent-child 관계가 아닌 각각의 컴포넌트끼리 데이터를 교류하기 위해 글로벌 이벤트시스템을 설정하는 방법.

### [](#App-js "App.js")App.js

  

#### [](#1-Action-만들기 "1. Action 만들기.")1\. Action 만들기.

action: 무슨 변화를 일으켜야 하는지 알려주는 객체.

```javascript

function setFilter(by) {

  return {type: 'SET\_FILTER', by};

}
```
  

#### [](#2-reducer-만들기 "2. reducer 만들기.")2\. reducer 만들기.

reducer: action으로부터 정보를 받아서 앱 상태를 어떻게 바꿀지 정의하는 객체. (action을 subscribe하고 있는놈)

초기값 설정  

```javascript

const initialState = {

  filterBy: ''

}
```
리듀서 만들기  

```javascript
function reducer(state = initialState, action) {

  switch (action.type) {

    case 'SET\_FILTER':

      console.log(\`Our filter was ${state.filterBy} but is now ${action.by}!`);

      return Object.assign({}, state, {

        filterBy: action.by

      })

    default:

      return state

  }

}
```

*   순수함수인 reducer는 반드시 parameter값에만 의존되어야 함.  
      
    

#### [](#3-store-생성 "3. store 생성")3\. store 생성

store: 앱의 state를 총괄적으로 관리하는 Single Source of Truth  

```javascript

const store = createStore(reducer)
```

store생성시 Root Reducer를 담아 전달함

> 여기서는 리듀서가 하나뿐이지만, 리듀서가 여러개일 경우 combineReducers()로 한개의 root reducer를 만들어 전달한다.

  

#### [](#4-connect "4. connect")4\. connect

\->리액트 컴포넌트를 redux store에 매핑 시키는 api

store의 state를 컴포넌트에서 받은 props에 매핑  

```javascript

const mapStateToProps = (state) => {

  return {

    filterBy: state.filterBy

  }

}

``` 

컴포넌트의 어떤 함수형 props를 실행했을 때 특정한 action을 dispatch하도록 설정

1

2

3

4

5

const mapDispatchToProps = (dispatch) => {

  return {

    updateFilter: (ev) => dispatch(setFilter(ev.target.value))

  }

}