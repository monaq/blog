---
title: 자바스크립트 개발자로서 알아야 할 10가지 면접질문(1)
tags:
  - 개발
  - 번역
date: 2017-12-21 11:11:11
---
### [](#1-자바스크립트-앱-개발자에게-있어-중요한-두-가지-프로그래밍-패러다임에-대해-말해볼-수-있는가 "1. 자바스크립트 앱 개발자에게 있어 중요한 두 가지 프로그래밍 패러다임에 대해 말해볼 수 있는가?")1\. 자바스크립트 앱 개발자에게 있어 중요한 두 가지 프로그래밍 패러다임에 대해 말해볼 수 있는가?

자바스크립트는 OOP(Object-Oriented Programming) 및 함수형 프로그래밍, 필수적/절차적 프로그래밍을 지원하는 다중 패러다임 언어이다.

자바스크립트는 프로토타입 상속으로서 OOP를 지원한다.

알아두면 좋은 것들:

*   프로토타입 상속 (프로토타입, OLOO)
*   함수형 프로그래밍 (클로저, 일급함수, 람다lambras)

주의할 점:

*   패러다임이 무엇인지 모르거나, 프로토타입이나 함수형 프로그래밍에 대한 언급이 없으면 안 됨.

더 공부해볼 것:

*   [The Two Pillars of JavaScript Part 1](https://medium.com/javascript-scene/the-two-pillars-of-javascript-ee6f3281e7f3) — 프로토타입 OOP.
*   [The Two Pillars of JavaScript Part 2](https://medium.com/javascript-scene/the-two-pillars-of-javascript-pt-2-functional-programming-a63aa53a41a4) — 함수형 프로그래밍.

  

### [](#2-함수형-프로그래밍이란-무엇인가 "2. 함수형 프로그래밍이란 무엇인가?")2\. 함수형 프로그래밍이란 무엇인가?

함수형 프로그래밍은 수학적 함수를 조합하여 프로그래밍 하고, 데이터 상태의 공유나 변경을 피한다.

1958년에 나온 Lisp는 함수형 프로그래밍을 지원하는 최초의 언어 중 하나였으며, lambda 미적분에 큰 영향을 받았다. Lisp 과 Lisp 계열의 많은 언어들이 오늘날에도 보편적으로 사용되고 있다.  
[Lisp 위키](https://ko.wikipedia.org/wiki/%EB%A6%AC%EC%8A%A4%ED%94%84)  
  
  
함수형 프로그래밍은 ‘자바스크립트의 두 가지 핵심적 요소’에서 필수적인 개념이다.  
일반적으로 쓰이는 몇 가지 함수형 유틸이 es5 에 추가되었다.

알아두면 좋은 것들:

*   순수함수(Pure function) / 함수 순수성
*   사이드 이펙트 피하기
*   함수는 심플하게 구성하기
*   함수형 언어의 예 : Lisp, ML, Haskell, Erlang, Clojure, Elm, F Sharp, Ocaml, Scala 등등..
*   FP를 지원하는 기능에 대한 언급: 일급함수, 고차함수, argument/value로서의 함수

주의할 점:

*   순수함수와 사이드 이펙트에 대한 언급이 없으면 안 됨.
*   함수형 언어의 예시를 들 수 없으면 안 됨.
*   FP를 사용할 수 있는 자바스크립트의 형태를 모르면 안 됨.

더 공부해볼 것:

*   [The Two Pillars of JavaScript Part 1](https://medium.com/javascript-scene/the-two-pillars-of-javascript-ee6f3281e7f3) — 프로토타입 OOP.
*   [Dao 의 불변성](https://medium.com/javascript-scene/common-misconceptions-about-inheritance-in-javascript-d5d9bab29b0a)
*   [소프트웨어 작성법](https://medium.com/javascript-scene/composing-software-an-introduction-27b72500d6ea)
*   [하스켈 뮤직 스쿨](https://haskell.cs.yale.edu/wp-content/uploads/2015/03/HSoM.pdf)

  

### [](#3-고전적인-상속과-프로토타입-상속의-차이점은-무엇인가 "3.고전적인 상속과 프로토타입 상속의 차이점은 무엇인가?")3.고전적인 상속과 프로토타입 상속의 차이점은 무엇인가?

**클래스 상속:** 인스턴스(청사진처럼 클래스를 묘사하는 것)를 상속하고 계층 관계를 구축한다. 이는 계층적 클래스 분류이다.

인스턴스는 일반적으로 생성자 함수를 통해 new 로 인스턴스화된다. 클래스 상속은 es6의 ‘class’를 사용할 수도 안 할수도 있다.

**프로토타입 상속:** 인스턴스는 다른 객체로부터 직접 상속받게 된다. 인스턴스는 일반적으로 팩토리 함수 또는 ‘Object.create()’를 통해 인스턴스화 된다. 인스턴스는 다양한 객체로 구성될 수 있기 때문에 선택 상속을 쉽게 할 수 있다.

> 자바스크립트에서 프로토타입 상속은 클래스상속보다 간단하고 유연하다.

알아두면 좋은 것들:

*   클래스: 밀접한 결합이나 계층 구조/분류를 만든다.
*   프로토타입 : 체인 상속, 프로토타입 위임, 함수 상속, 객체 구성에 대한 것.

주의할 점:

*   클래스 상속에 대한 프로토타입 상속과 컴포지션에 대한 선호도를 어필

  

### [](#4-함수형-프로그래밍과-객체지향-프로그래밍의-장점과-단점은-무엇인가 "4. 함수형 프로그래밍과 객체지향 프로그래밍의 장점과 단점은 무엇인가?")4\. 함수형 프로그래밍과 객체지향 프로그래밍의 장점과 단점은 무엇인가?

*   OOP의 장점 : 객체의 기본개념을 이해하기가 쉽고 메소드 콜의 의미를 해석하기가 쉽다. OOP는 선언형보다 명령형 스타일을 사용하는 경향이 있다. 이 형식은 컴퓨터가 따라야 할 방향과 똑같이 진행된다.
    
*   OOP의 단점 : OOP는 공유된 상태에 의존적이다. 객체와 행위는 일반적으로 동일한 엔티티에 고정되어 있으며, 비결정적(non-deterministic) 순서로 임의의 수의 함수에서 무작위로 액세스할 수 있으므로 바람직하지 않은 동작이 발생할 수 있다. 경쟁 조건(race condition)같은 예가 그것이다.
    
*   FP의 장점 : 함수형 패러다임을 이용해서, 상태 공유 또는 사이드 이펙트를 피할 수 있다. 이는 같은 리소스에 대해 경쟁하는 어러 함수 때문에 생길 수 있는 버그를 제거한다. point-free형(일명 암묵적 프로그래밍) 함수를 사용하면 OOP에 비해 함수를 훨씬 근본적으로 단순화하고 재구성 가능하게 만들 수 있어 재사용이 용이하다.
    

  
  
FP는 또한 작업의 단계별 명령을 맞추는 대신 선언형과 의미구조 스타일을 선호하고 ‘무엇을 할 것인가’에 집중하는 경향이 강해서, 해야할 일에 집중하여 기본적인 기능이 ‘어떻게 처리될 것인가’를 알려준다.  
이는 리팩토링과 성능 최적화에 엄청난 도움이 되며 전체 알고리즘을 코드 변경이 거의 없는 상태에서 보다 효율적으로 대체할 수 있다. 메모이제이션이나 엄격평가(eager evaluation) 대신 지연평가를 사용하는 예를 들수 있다.

순수함수를 사용하는 계산의 경우 리소스 충돌이나 레이스 컨디션 등을 우려하지 않고도 다중 프로세서나 분산 컨퓨팅 클러스터 전반적으로 쉽게 확장 가능합니다.  
  
  
**FP의 단점 :** Point-free 또는 대형 프로젝트 조합의 경우 FP의 과도한 사용은 결과코드가 더 추상적으로 지정되고, 간단하며 덜 구체적이기 때문에 가독성이 떨어지는 위험을 잠재적으로 가지고 있다.  
많은 사람들이 함수형 프로그래밍보다는 OOP 및 명령형 프로그래밍에 익숙하기 때문에 함수형 프로그래밍의 일반적인 사용법조차 새로운 팀원에게는 혼란스럽게 받아들여질 수 있다.

FP는 OOP보다 학습 곡선이 가파르다. 왜냐하면 OOP의 광범위한 인기로 인해 OOP 언어나 학습자료는 훨씬 편안하게 공유될 수 있었지만, FP 언어는 훨씬 학문적이고 공식적인 경향이 있었다.  
FP 개념은 lambda 미적분, 대수학 및 범주 이론의 관용구나 표기법을 어떻게 사용하는지에 대해 논한다. 이 모든 것이 사전 지식을 필요로 한다.

알아두면 좋은 것들:

*   상태 공유와 관련된 문제에 대한 것들, 동일한 리소스에 대해 경쟁하는 다양한 것들, 기타 등등..
*   학습 곡선의 차이에 대한 인식
*   사이드 이펙트와 프로그램 유지 관리에 미치는 영향
*   고도의 함수 코드베이스이기 때문에 학습곡선이 높음
*   고도의 OOP 코드베이스가 동등한 FP 코드베이스와 비교했을 때 변화하기 쉽고 깨지기도 쉬움을 인식
*   불변성은 접근이 매우 쉽고 유연한 상태 히스토리를 제공하여 무한한 undo/redo, rewind/replay, 시간 이동 디버깅 등의 기능을 쉽게 추가할 수 있다. 불변성은 어느 패러다임에서든 가능하지만 공유된 상태가 많은 객체가 확산되는 것은 OOP의 구현을 복잡하게 한다.

주의할 점:

*   한 패러다임 또는 다른 패러다임의 단점을 열거할 수 없으면 안 된다. 어느 스타일로든 코딩해 본 경험이 있다면 제한사항 중 일부에 부딪혀 본 경험이 있을 것이다.

더 공부해볼 것:

*   [The Two Pillars of JavaScript Part 1](https://medium.com/javascript-scene/the-two-pillars-of-javascript-ee6f3281e7f3) — 프로토타입 OOP.
*   [The Two Pillars of JavaScript Part 2](https://medium.com/javascript-scene/the-two-pillars-of-javascript-pt-2-functional-programming-a63aa53a41a4) — 함수형 프로그래밍.

  
  
이는 [https://medium.com/javascript-scene/10-interview-questions-every-javascript-developer-should-know-6fa6bdf5ad95](https://medium.com/javascript-scene/10-interview-questions-every-javascript-developer-should-know-6fa6bdf5ad95) 를 번역한 것입니다.