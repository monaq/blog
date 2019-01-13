---
title: map 이해하기
tags:
  - 번역
  - 동영상
date: 2017-11-19 11:11:11
---
## [](#Map-이해하기 "Map 이해하기")Map 이해하기

### [](#map-함수의-이해와-정의 "map 함수의 이해와 정의")map 함수의 이해와 정의

map 메소드는 배열의 모든 요소들에 함수를 적용한 후 새로운 배열을 리턴한다.

예를 들어 보자

```javascript

let newArray = oldArray.map((val, index, arr) => {

  // 엘리먼트를 새로운 배열로 반환

})

```
*   newArray - 반환된 새로운 배열
*   oldArray - map 함수를 실행하는 배열
*   val - 처리되는 현재 값
*   index - 처리되는 값의 현재 인덱스
*   arr - 원래 배열

### [](#Map-vs-for문 "Map vs for문")Map vs for문

map 함수를 for문과 같은 것으로 이해할 수도 있다. 값을 변환하기 위해서라는 점에 있어서는 그렇게 생각할 수도 있다.

다음 예제를 보자.

```javascript

var arr = \[1, 2, 3, 4\]

var plus5 = \[\]

for(var i = 0 i < arr.length i++) {

    plus5\[i\] = arr\[i\] + 5

}

// plus5 = \[6,7,8,9\]

```

이 코드는 이전 배열에 각각 5를 더하는 새로운 배열을 생성한다. 이 코드와 동일한 결과를 얻을 수 있는 훨씬 쉬운 방법이 map()이다.

이 코드를 map() 으로 변환하기 위해서는 단순한 배열을 하나 선언한다  

```javascript

let arr = \[1,2,3,4\]
```

*   arr - 우리가 매핑할 배열이다. 각 값에 5를 더한 값을 반환한다.

```javascript

let plus5 = arr.map((val, i, arr) => {

  return val + 5

})

```

이제 두 개의 배열을 로그에 출력해 보자. arr 배열은 변경되지 않은 채 plus5 배열이 새로운 값을 갖게 된다.  

```javascript

arr = \[1,2,3,4\]

plus5 = \[6,7,8,9\]

```

끝! 더 이상 배열에 직접 값을 더할 필요가 없어졌다. map() 함수를 이용하면, 설계한 것을 정의만 하면 된다. map() 함수가 나머지는 다 알아서 해준다.

### [](#Map-예제-2 "Map 예제 2")Map 예제 2

이 예제에서는 value와 index 인자를 사용할 것이다.

지난번과 같은 기본적인 배열로 시작하자.  

```javascript

let arr = \[1,2,3,4\]
```
하지만 이번에는 객체를 반환할 것이다. 이 객체는 해당 인덱스에 인덱스와 값을 포함한다. 이 작업을 위해, 다음과 같은 i 인자를 사용한다.


```javascript
newArr = arr.map ((val, i, arr) => {

  return { 

    value : val, 

    index : i 

  }

})

```

이렇게 하면 newArr을 통해 새로운 객체 배열이 생성된다.

```javascript
arr = \[1,2,3,4\]

newArr = \[

  {value: 1, index: 0},

  {value: 2, index: 1},

  {value: 3, index: 2},

  {value: 4, index: 3}

\]

```

\*\* 다행히 map() 배열 내에서 반환해 주는 것은 새로운 배열을 만드는 데 사용한다. 현재 value, 현재 index 또는 전체 배열을 활용해서 반환할 요소를 정할 수 있다.  
정적인 문자열을 반환하는 것도 할 수 있다(실제로 아무런 연결점도 없지만).

```javascript

let arr = \[1,2,3,4\]

newArr = arr.map (() => { 

  return 'cats' 

})

// newArr = \[ 'cats', 'cats', 'cats', 'cats'\]

```

### [](#Map-예제-3 "Map 예제 3")Map 예제 3

지금까지의 모든 예제에서는 원래 배열의 모든 값을 변환했다. 만일 배열의 값들 중 일부만 변환하고 싶다면 어떻게 해야 할까?

이 문제를 해결할 수 있는 방법에는 여러가지가 있다. 가능한 해결책을 살펴보자.

이 예제에서도 단순한 배열을 선언해 보겠다.  

```javascript
let arr = \[1,2,3,4\]
```

짝수를 2배 곱하고 홀수는 그대로 두는 코드를 작성해 보자. 이를 위해 map() 함수 내에 로직을 이렇게 추가할 수 있다.  

```javascript

newArr = arr.map ((v, i, a) => { 

  return v % 2 === 0 ? v \* 2 : v

// newArr = \[1,4,3,8\]
```
끝이다. 짝수 값은 2배가 되고 홀수는 그대로 유지되었다.

위 코드가 이해가 되지 않는다면 다음과 같이 작성할 수 있다.  

```javascript
newArr = arr.map ((v, i, a) => { 

  if (v % 2 === 0) { 

    return v \* 2 

  } else { 

    return v 

  } 

})

// newArr = \[1,4,3,8\]
```

위와 똑같은 코드를 읽기 쉽개 조금 확장해 보았다.

먼저 인자를 2로 나는 값의 나머지가 0인지를 확인한다. 이것은 숫자가 짝수인지 홀수인지를 판별하는 가장 간단한 방법이다.  
짝수는 항상 나머지 0을 가지고, 홀수는 항상 나머지 1을 가진다.

나머지가 0이면 숫자가 짝수임을 의미하므로, 이 케이스에서는 현재 값을 2배 해서 반환한다.  
나머지가 1이면 숫자가 홀수임을 의미하므로, 이 케이스에서는 v값을 변경하지 않은 채 반환한다.

\*\*원본: ([https://codeburst.io/learn-understand-javascripts-map-function-ffc059264783](https://codeburst.io/learn-understand-javascripts-map-function-ffc059264783))