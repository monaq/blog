---
title: 자바스크립트의 언어적 개념 9
tags:
  - 개발
  - javascript
date: 2019-01-09 11:11:11
---
# 오브젝트
## 9.1 프로퍼티 리스트
* 책 참고.
## 9.2 Object 분류
* 오브젝트: 0개 이상의 프로퍼티로 구성되는 오브젝트
* 빌트인 오브젝트: 렌더링 과정에서 자바스크립트가 생성하는 오브젝트
* 네이티브 오브젝트: 자바스크립트 프로그램을 실행할 때 생성되는 오브젝트
* 호스트 오브젝트: 호스트 환경에서 자바스크립트 실행 환경을 보완, 지원하기 위해 제공하는 오브젝트(ex. DOM에서 제공하는 오브젝트)

## 9.3 new Object()
* 인스턴스를 생성하여 반환한다.
```javascript
var obj = new Object();
console.log(obj); // [object Object]

var numObj = new Number(123);
var objNumber = new Object(numObj);
console.log(numObj === objNumber); // true

var obj = new Object(1234);
console.log(typeof obj); // object
console.log(obj); //1234

console.log(new Object(true)); //true
var nodes = document.getElementByTagName('script');
console.log(new Object(nodes[0])) // [object HTMLScriptElement]
```
* 책 참고
## 9.4 Object()
* Object() 와 new Object()로 생성한 겂은 같다.
## 9.5 문자열 표시 반환
* toString() 은 오브젝트 타입을 문자열 표시 형태로 변환해 반환한다.
```javascript
console.log(Object().toString());

var obj = new Object();
console.log(obj.toString.call(new Number())); // [object Number]
console.log(obj.toString.call(Undefined)); // [object Undefined]
console.log(obj.toString.call(null)); // [object Null]

```
### toString() 의 특징
```javascript
var obj = new Number(123);
console.log(obj.toString()); //123
```
상속을 받았는데 빌트인 오브젝트의 toString()메소드가 호출되지 않는 것은 각 오브젝트에 toString 메소드가 있기 때문이다.(만일 이렇다면 원시타입을 반환하겠죠?)
toString()메소드가 호출되면 각 오브젝트에 속한 toString()메소드를 먼저 찾는다.
## 9.6 지역화 문자로 변환
* 지역화 문자로 변환한 값 반환
ex) IE브라우저로 한국에서 12345 변환 => 12,345.00
## 9.7 프리미티브 값 반환
* object 위치에 인스턴스를 지정하며 인스턴스의 원시 값을 반환한다.
* Boolean, Date, Number, String오브젝트는 [[PrimitiveValue]]값이 반환되도록 하기 위해 오브젝트에 valueOf메소드를 갖고 있다.
## 9.8 프로퍼티 소유 여부
* hasOwnProperty 메소드는 프로퍼티 소유여부를 Boolean으로 반환
```javascript
var obj = Object();
ojb.pty = 'check';
console.log(obj.hasOwnProperty('pty')); //true
```
### prototype chain, 상속
prototype에 오브젝트를 연결하는 것과 인스턴스를 연결하는 것은 다르다.
오브젝트 연결은 [name: value]형태를 연결한 것이고 인스턴스 연결은 new 연산자로 생성한 인스턴스를 연결한 것이다.
인스턴스가 연결된 형태를  prototype chain이라고 한다.
## 9.9 prototype에 오브젝트 존재 여부
isPrototypeOf 메소드는 prototype에 오브젝트가 존재하는지 여부를 Boolean값으로 반환
## 9.10 프로퍼티 열거 가능 여부
propertyEnumerable 메소드는 프로퍼티의 열거 가능 여부를 반환한다.
```javascript
var obj = new Object();
obj.value = '값';
console.log(Object.keys(obj)); // [value]
console.log(obj.propertyIsEnumerable('value')); // true

Object.prototype.add = 'plus';

var addObj = new Object();
console.log(addObj.add); // plus
console.log(addObj.propertyIsEnumerable('add')); // false
```
