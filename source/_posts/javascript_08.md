---
title: 자바스크립트의 언어적 개념 8
tags:
  - 개발
  - javascript
date: 2019-01-02 11:11:11
---

# 자바스크립트의 언어적 개념

## 8.1 자바스크립트 기준과 범위
### 자바스크립트 기준과 범위
자바스크립트는 객체지향 프로그래밍(OOP: Object Oriented Programming) 언어이다. 객체 지향 프로그램을 구현하는 방법은 언어마다 차이가 있다. 사전 컴파일 언어와 스크립트 언어는 환경이 다르므로 구현 방법이 다르므로 자바스크립트의 경우 OOP의 일부 개념을 지원하지 않는다.

그러나 최근 자바스크립트에서도 OOP의 개념을 사용하여 개발하고 있으므로 알아 두는 것이 좋겠다.
#### OOP의 기본 개념
* 캡슐화: 외부에서 접근하지 못하게 private 화 하는 것
* 다형성: 상속을 통해서 다른 동작을 가능하게 해 준다. 오버라이딩/오버로딩을 통해 가능하다. 부모클래스에서 상속받은 속성을 재창조해서 사용하는 것이 다형성이다. 같은 행위를 목적에 맞게 다양한 기능 수행을 할 수 있도록 바꾸는 것.
* 추상화: 추상 클래스를 만든다. 개발할 요소들을 모두 클래스에 담고 재사용할수 있게 만들 수 없다. 공통적인 메소드를 추출하여 추상화 하는 것이 추상화이다.
* 상속성: 기존 클래스의 기능을 가져와 만들면서도 새롭게 만든 클래스에 새로운 기능을 추가할 수 있는 것.

### 객체

* 행위(Behavior)와 속성(Attribute)을 갖고 있고 실체가 존재한다.
```
사람 = {
    eat: function(fruit) {
        eat fruit();
    },
    quantity: 1
}
// eat 는 과일을 먹는 '행위'를 나타내며 quantity는 과일 1개를 나타내는 이름이다
// eat에 접근하면 먹는 행위를 실행할 수 있고
// quantity에 접근하면 과일 1개 값을 구할 수 있다.
```

### 프로퍼티
```javascript
sports = [soccor: '11']
// 11을 구하려면 우선 오브젝트인 sports를 알아야 한다.
// 다른 오브젝트, 예를 들어 game = [soccer: '11'] 과 같이 존재할 수 있기 때문
```
* 오브젝트에는 프로퍼티 이름이 하나만 존재해야 한다.
* es5 스트릭트 모드에서는 오브젝트에 같은 이름이 있으면 오버라이딩 된다.
### 오브젝트와 인스턴스
* object 를 사용하여 Object를 생성하면 Object가 반환됨
* new 연산자를 사용하여 오브젝트를 생성하여 변수에 할당할 수 있으며, 이 할당된 오브젝트가 인스턴스 이다.
* 인스턴스를 생성하는 목적: 인스턴스마다 다른 값을 유지하고, 제어하기 위해 인스턴스를 생성한다.
### 함수와 메소드
* 함수는 오브젝트에 속하며, 행위를 나타낸다.
* 함수 안에 함수의 목적 달성을 위한 코드를 작성한다.


## 8.2 빌트인
* 자바스크립트를 컴파일하고 생성하는 단계.
* 빌트인의 목적: 개발자 프로그램이 실행되기 전에 미리 생성되어 프로그램에서 사용할 수 있게 환경을 만들어주는 역할임.
### 빌트인 연산자
### 빌트인 데이터 타입
* Undefined, Null, Boolean, Number, String
### 빌트인 오브젝트
* Global, Object, Function, Array, String, Boolean, Number
* Math, Date, RegExp, JSON
* Error 처리용 오브젝트

## 8.3 빌트인 오브젝트
* Global, 
* Object, 
* Function, 
* Array, 
* String, 
* Boolean, 
* Number

* Math
* Date
* RegExp
* JSON

### Object 인식
#### 객체지향 형식
```javascript
var obj = new String();
var result = obj.concat('sport', 'soccer', 11);
console.log(result); //sportssoccer11

obj = new Array();
result = obj.concat('sports', 'soccer',11);
console.log(result); // ['sports', 'soccer', 11]

```

#### 자바스크립트 형식
```javascript
var result = 'sports'.concat('soccer', 11);
console.log(result); //sportssoccer11

result = ['sports'].concat('sports', 'soccer',11);
console.log(result); // ['sports', 'soccer', 11]

```
* 이처럼 데이터 타입에 의해 오브젝트에 속한 메소드가 호출되는 메커니즘을 뒷받침하는것이 빌트인 타입, 빌트인 오브젝트이다.

## 8.5 prototype 오브젝트
```javascript
// concat 메소드를 오브젝트 형태로 표현
String: {
    length: 값,
    concat: function() {},
    indexOf: function() {}
}
```
* 위와 같이 작성하면 각각의 프로퍼티와 메소드가 구분되지 않기 때문에  prototype을 사용하여 메소드를 구분한다.
```javascript
// concat 메소드를 prototype 형태로 표현
String.length
String.prototype.concat
String.prototype.indexOf
```
```javascript
// concat 메소드를 prototype 형태로 표현
String: {
    length: 값,
    prototype: {
        concat: function() {},
        indexOf: function() {}
    }
}
```
* 프로토타입은 이외에더 다른 오브젝트를 상속받아 연결하거나 prototype에 연결된 프로퍼티를 공유할 때 사용함.(OOP에서의 상속)

## 8.6 new 연산자
```javascript
var str = new String(); // 스트링 객체 반환
var Sports = function(){}; 
var spts = new Sports(); // function 객체 반환
```
* new 연산자는 인스턴스를 생성하여 반환한다.
* Number는 오브젝트를 생성하지 않고 Number('123')일때 문자열 123을 숫자로 변환하여 반환 한다.
### fallback (pollyfill)
* 크로스브라우징을 할 때 같은 이름의 메소드를 만들어 빌트인 오브젝트의  prototype에 연결하면 된다.
## 8.7 constructor
* constructor가 있어야 새로운 오브젝트(인스턴스)를 생성할 수 있다.

## 8.8 instanceOf 연산자
```javascript
var obj = new Object();
console.log(obj == Object); //false
console.log(obj instanceof Object) //true
```
* 인스턴스의 오브젝트 형식을 비교하려면  instanceOf 연산자를 사용한다.

