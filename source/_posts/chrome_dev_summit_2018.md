---
title: 제가 Chrome Dev Summit 2017 영상을 다 보고 왔으니, 당신은 볼 필요가 없어요.
tags:
  - 번역
date: 2017-11-02 11:11:11
---
> 이 글은 [https://redfin.engineering/i-watched-all-of-the-chrome-dev-summit-2017-videos-so-you-dont-have-to-9b62a593c3cb](https://redfin.engineering/i-watched-all-of-the-chrome-dev-summit-2017-videos-so-you-dont-have-to-9b62a593c3cb) 을 발번역 한 것입니다. 원본과 함께 읽으시면 이해가 쉽습니다.

[](#몇-가지-발표와-PMA홍보가-있었습니다 "몇 가지 발표와 PMA홍보가 있었습니다.")몇 가지 발표와 PMA홍보가 있었습니다.
-------------------------------------------------------------------------

10 시간 분량의 Chrome Dev Summit 2017 영상은 온라인에서 확인할 수 있습니다.  
([https://www.youtube.com/watch?v=1-g1rvkORQ8&list=PLNYkxOF6rcICUD5nBfRdAR6Fveosnqa5m](https://www.youtube.com/watch?v=1-g1rvkORQ8&list=PLNYkxOF6rcICUD5nBfRdAR6Fveosnqa5m))

너무 기니까 요약하자면: 구글은 PWA를 구축하고 javascript 파일 크기를 줄이기를 원하고 있습니다. 또한, 웹 컴포넌트를 사용하고 자동완성을 형성하고 싶어합니다.

구글은 다음과 같은 몇 가지 기능을 발표했습니다.

& 결제, 인증, 안드로이드에서도 신뢰할 수 있는 웹 액티비티들, 크롬 개발도구와 크롬 유저 경험에 대한 리포트 등등…

이에 대한 Reddit에서의 논의는 여기서 볼 수 있습니다([https://www.reddit.com/r/programming/comments/7910rg/i\_watched\_all\_of\_the\_chrome\_dev\_summit\_2017/](https://www.reddit.com/r/programming/comments/7910rg/i_watched_all_of_the_chrome_dev_summit_2017/))

이에 대한 Hacker News의 논의는 여기서 볼 수 있습니다([https://news.ycombinator.com/item?id=15575109](https://news.ycombinator.com/item?id=15575109))

일반적으로 구글은 Chrome Dev Summit 에서 다음과 같은 내용을 발표합니다.

*   사람들이 사용했으면 하는 웹기술 홍보
*   뉴스 발표 / 새로운 것에 대해서 또다시 발표하기 (가끔씩 이미 있는거랑 섞여있음)
*   웹 개발자를 위한 실질적 조언 공유

하지만 이 “공지 사항”은 종종 이미 있는 기술들을 홍보하고 싶어서 다시 발표하는 것입니다.  
떄로는 이들은 실용적이지 않은 웹기술들을 옹호합니다. 예를 들어 베타버전에서 나올 새 기능이나 크롬에서만 작동하는 기술들 같은 것 말입니다.

### [](#구글이-원하는-것 "구글이 원하는 것")구글이 원하는 것

#### [](#프로그레시브-웹앱을-구축하는-것 "* 프로그레시브 웹앱을 구축하는 것")\* 프로그레시브 웹앱을 구축하는 것

구글은 Service Worker를 이용해 오프라인일 때도 앱이 기능하게 개발해 주었으면 합니다. 하지만 Service Worker가 iOS에서 작동을 안 하기 때문에 문제가 잇습니다.  
드디어 애플이 올해 초에 작업에 들어갔습니다. 운이 좋으면 iOS 12에서 사용 가능할 수도 있을 것입니다.

#### [](#javascript-로-구현된-웹사이트의-전송량을-줄이기 "* javascript 로 구현된 웹사이트의 전송량을 줄이기")\* javascript 로 구현된 웹사이트의 전송량을 줄이기

구글은 100달러 정도의 저렴한 안드로이드 폰에서 ‘time to interactive’ 이벤트를 실행하는 것을 목표로 합니다. 여유있는 서구권 국가의 웹개발자들은 성능이 훨씬 뛰어난 아이폰이나 고급 안드로이드 디바이스를 사용하는 경향이 있습니다.  
(아이폰 8은 8mb의 l2 cpu 캐시를 보유하고 있으며, 최근에 출시된 안드로이드 폰들도 일반적으로 l2캐시는 탑재되어 있지 않다)  
저렴한 폰의 경우 일반적으로 1mb의 압축되지 않은 자바스크립트나 150kb의 gzipped 파일만 제공합니다. 특히 신흥시장에 많은 제품이 팔릴 경우가 아니면 모든 웹 개발자가 이런 리미트에 맞춰 개발하게 하기는 쉽지 않습니다.  
구글에서 권장하는 목표를 달성하려면 잘 작성된 js 프레임워크를 포기하고 새로 만들어야 할 때도 있습니다.

#### [](#웹-컴포넌트-사용 "* 웹 컴포넌트 사용.")\* 웹 컴포넌트 사용.

(여기서, 이것은 custom element와 shadow DOM 을 의미하며 HTML import는 포기한 것 같습니다.)  
특히 Polymer를 사용하고 싶어하는 것 같습니다. 문제는, 웹 컴포넌트 API가 리액트와 비교해서 직접적으로 사용하기가 매우 어렵다는 점입니다.  
그것은 프레임워크 시장에서 폴리머를 다시 끌어내고 있습니다. Svelte, Skate 나 Stencil 같은 다른 WC기반 프레임워크에서는 WC에서 추상화하여 편집 대상으로 다룹니다.  
(WCs는 다른 큰 문제점을 가지고 있는데, shadow DOM에 대한 서버측 렌더링 방법이 존재하지 않는다는 겁니다. 특히, 서버 렌더링된 비 WC출력에서 클라이언트측의 WC를 합칠 수 있는 효율적인 방법이 없습니다)  
또한 구글은 WC가 권장 목표를 달성하기 위한 중요한 전략이라고 느끼고 있습니다. 플랫폼을 사용하고 js에서 그것을 다시 재발생(reinvent)시키지 않는다면 믾은 자바스크립트 byte를 절약할 수 있습니다.

#### [](#폼을-만들-때-자동완성을-지원하도록-해야-합니다-특히-로그인-및-자동완성의-경우 "*폼을 만들 때 자동완성을 지원하도록 해야 합니다( 특히 로그인 및 자동완성의 경우)")\*폼을 만들 때 자동완성을 지원하도록 해야 합니다( 특히 로그인 및 자동완성의 경우)

얼마나 많은 인기 쇼핑몰들이 오토필을 무시했는지 알면 충격적입니다.  
이것은 모바일 브라우저에서 특히 중요합니다. 최근 몇 년 동안 크롬은 Credential Management API와 Payment Request API를 비롯한 새로운 자동완성 기능을 추가했지만, 크로스브라우징 지원이 좋지 않아 이 기능을 사이트에서 채택하기는 좀 시간이 걸립니다.

### [](#발표-내용 "발표 내용")발표 내용

#### [](#결제-이미-있는-거랑-비슷하지만-조금-다릅니다 "결제: 이미 있는 거랑 비슷하지만 조금 다릅니다.")결제: 이미 있는 거랑 비슷하지만 조금 다릅니다.

Google Payment API가 언급됩니다. Google Checkout을 Google Wallet으로 대체하고 난 후, Android Pay를 교체하고 나서 문서에서 대담하게도 이를 “Google에서 결제하는 가장 새로운 방법”이라고 불렀습니다.  
Google Payment API는 안드로이드 크롬에서만 작동합니다. 표준이긴 하지만 재대로 지원되지 않는 결제요청 API와 통합되었습니다.  
시간이 흐르면 다른 플랫폼 및 다른 브라우저에서도 지원이 가능하길 바랍니다.

동시에, Payment Request API는 모든 Chrome 플랫폼에서 사용할 수 있지만 예전엔 안드로이드에서만 사용할 수 있다고 발표했었습니다.

#### [](#인증-이미-있는-것과-비슷하지만-조금-다릅니다 "인증: 이미 있는 것과 비슷하지만 조금 다릅니다.")인증: 이미 있는 것과 비슷하지만 조금 다릅니다.

“자동 로그인”과 “One-tap Sign Up” 두 가지 기능이 소개되었습니다.  
물론, 그동안 구글 로그인을 통해 구글에 가입하거나 로그인할 수 있었습니다. (그들은 간단하게 “Google+ 로 로그인” 이라고 부릅니다.)  
하지만 이 버전은 스크린 아래애서 애니메이션이 튀어나와 사용자가 구글에 로그인 할 수 있게 해 줍니다.  
새로운 “one-tap” 플로우는 Credential Management API 를 polyfill하여 iOS에서도 사용할 수 있도록 고안되었습니다.

#### [](#신뢰할-수-있는-웹-액티비티-Android-앱의-PWA-tab "신뢰할 수 있는 웹 액티비티 : Android 앱의 PWA tab")신뢰할 수 있는 웹 액티비티 : Android 앱의 PWA tab

신뢰할 수 있는 웹 액티비티는 URL 표시줄을 출력하지 않고 Android 앱에서 Chrome 의 커스텀 탭을 띄울 수 있는 방법입니다. 안트로이드 앱에서 맞춤 웹사이트를 스크린에 띄우고 구글 플레이 스토어에서 안드로이드 앱으로 PWA를 더욱 쉽게 패키징 할 수 있도록 설계되었습니다.

#### [](#Chrome-개발자-도구에-대한-개선사항 "Chrome 개발자 도구에 대한 개선사항")Chrome 개발자 도구에 대한 개선사항

대부분의 개발자 도구와 마찬가지로 설명하기가 어려운데, 그것이 어떻게 작동하는지 확인하려면 비디오를 봐야 합니다. 그들은 CSS 그리도 레이아웃, “local override”(개발자 도구에 저장된 Greasemonkey “사용자 스크립트”를 만드는 방법)  
, 새로운 실시간 퍼포먼스 모니터링, 유사한 이벤트들을 필터링하고 그룹핑하는 console.log 향상 기능, 그리고 어플리케이션 탭의 PWA개선 사항을 보여 줍니다.

#### [](#Chrome-사용자-환경-보고서 "Chrome 사용자 환경 보고서")Chrome 사용자 환경 보고서

크롬 사용자환경 보고서는 BigQuery입니다. 이는 상위 1000개의 웹사이트에 대한 실제 사용자 모니터링에 대한 쿼리가 가능합니다.  
그것을 누가 어떻게 사용할지는 잘 모르겠지만, 누군가는 쿨하게 사용하기를 바랍니다.

### [](#발표-내용-1 "발표 내용")발표 내용

*   키노트(Keynote) - Ben Galbraith, Dion Almaer
*   웹 경험을 위한 새로운 바 툴(The New Bar for Web Experiences) - Thao Tran, Chris Wilson
*   운영체제와의 통합(Integrating with Operating Systems) -Owen Campbell-Moore
*   진보된 웹앱으로 킥스타트 하기 (Kickstarting Your Journey to Progressive Web Apps) - Ewa Gasperowicz
*   디폴트로 빨라지기: 최신 베스트 로딩 프랙티스 (Fast by Default: Modern Loading Best Practices) - Addy Osmani, Ilya Grigorik and Bryan McQuade
*   Workbox: 유연한 PWA 라이브러리 (Workbox: Flexible PWA Libraries) - Jeff Posnick
*   워드프레스 + PWA(Wordpress + PWAs) - Surma and Dan Walmsley
*   점진적 이커머스 개선(Progressively Improving E-Commerce)- Sam Dutton and Rowan Merewood
*   최신 미디어 환경 구축(Building a Modern Media Experience) - Francois Beaufort and John Pallett
*   전 세계를 위한 웹(The Web for the Entire World) - Tal Oppenheimer
*   최신 툴링, 테스팅, 그리고 자동화(Modern Tooling, Testing, and Automation) - Eric Bidelman and Paul Irish
*   웹 로딩의 미래 (The Future of Loading on the Web) - Sam Saccone
*   V8의 오늘날과 미래(V8 Today and in the Future) - Thomas Nattestad
*   Real World WebAssembly(Real World WebAssembly) - Alex Danilo and Deepti Gandluri
*   엔드투엔드 폴리머 앱과 최신 웹 플랫폼(End-to-End Polymer Apps and the Modern Web Platform) - Taylor Savage
*   lit-HTML(lit-HTML) - Justin Fagnani
*   앱 없이 미디어 만들기(Creating Media Without an App) - Mat Scales, Jennifer Lin, Peter Shin
*   VR과 AR(The Future of Immersive Experiences on the Web with VR and AR) - Josh Carpenter and Brandon Jones

### [](#QnA "QnA")QnA

질답시간이 대부분의 발표보다 더 좋았다고 생각합니다. 제 의견이고요. 제 질문에 대답을 많이 해줬기 때문은 아닙니다 :)

진행자 : Chris Wilson  
패널 : Darin Fisher, Parisa Tabriz, Grace Kloba, Thao Tran, Tal Oppenheimer, Matt McNulty, Alex Komoroske 및 Alex Russell

*   AMP vs PWA? : 목표는 빠른 웹입니다.
*   올해 PWA 서밋이 없는 이유는 뭐죠? : PWA 뿐만 아니라 다 없어요.
*   Javascript binary AST를 지원합니까: 좀 다른 방식이 있습니다, Service Worker가 파싱되고 컴파일 된 결과를 캐싱하는 거 말고도요.  
    바이너리 AST는 장시간에 걸친 결과를 가져오며, 그걸 우리가 완벽하게 이해하진 못합니다.
*   바탕화면에서 “홈 스크린에 추가”하는 것은? : 지금 가능하긴 한데, 묻혀 있습니다. Owen은 뭔가 새로운 일이 벌어지는 스크린샷을 보여 주었었죠. 몇 달 안에 보실 수 있을 겁니다. (Chrome flag에서 찾아보세요)
*   ES6를 트랜스파일 하거나 직접 써야 하나요? : User는 어떤 사람이죠? 당신의 유저들이 그걸 지원하면 직접 써도 되고요, 아니면 트랜스파일 해야죠.
*   여러 팀이 렌더링 엔진이나 하나의 큰 브라우저에서 작업할 순 없나요? : 웹 개발자로서, 하나의 브라우저가 필요하죠. 하지만 경쟁에 있어서, 하나의 큰 브라우저는 정체하거나 멈출 수 없다는 것을 의미합니다.  
    브라우저 전쟁은 지금은 훨씬 사그라들었습니다. 우리는 서로 협력하면서 좋게 일하고 있습니다. 이러한 기술적 문제에 접근할 때, 다양성에는 고유한 가치가 있다고 할 수 있습니다.
*   PWA 및 안드로이드 인스턴트 앱에 대한 구글의 정체성 위기는 어떻게 될까요? : 구글 내부에서는 경쟁적인 분위기를 중시합니다. 세상엔 좋은 선택지들이 많습니다,.
*   Chrome에서만 돌아가는 사이트는 어떤가요? : 저희는 그런 걸 좋아하지 않아요. 저희는 내부적으로 그런 것들을 방지하려고 노력합니다.
*   왜 GPS에 PWA를 설치할 수 없나요? : 음, 그건 할 수 있습니다. 이제는 Trusted Web Activities를 통해서 더 쉽게 할 수 있죠.
*   향후 10년간 무엇을 가장 내세울 만 한가요?:  
    \-웹이 모바일 이후에 form factor의 다음 변화에서도 생존할 수 있도록 합니다.  
    \-건강한 경쟁이 가장 자랑스러워요. -사용자를 우선시합니다. -우리는 모든 사용자를 위한 웹을 구축합니다. -한번 구축하면 어디서나 작동할 수 있습니다. -다음 세대의 플랫폼 핸들링. -HTTPS의 성장 및 안전하고 검사 가능한 PKI도입. -장기간 근무

#### [](#프레임워크-패널 "프레임워크 패널")프레임워크 패널

*   프레임워크에 가장 도움이 되는 새로운 브라우저 기능은 뭔가요?:

\-DOMChangeList.

\-맞아요. DOMChangeList 및 Observables

\-웹 작업자를위한 향상된 개발 도구.

\-Real weak references

\-WC가 네이티브 컴포넌트를 더 많이 수행하도록 허용하지 않습니다.

\-모든 요소를 ​​비동기로 만듭니다. Async append, DOMChangeList와 유사합니다.

*   프레임워크를 선택하려면 어떤 기준으로 봐야 하나요? : byte의 관점에서 얼마나 많은 headroom에 필요한가- 를 기준으로 보면 됩니다
*   어떻게 interop을 합니까? : 뭐 괜찮을거에요. Vue가 개척할 거니까요. Preact는 Vue 구성 요소를 가져올 수 있어요.  
    \-우리 모두 웹 컴포넌트를 컴파일하는 데 동의합니다.  
    \-WC는 interop을 수행 할 수 있게 설계되었습니다.  
    \-Angular 컴포넌트가 WC를 넘어서면 좋을 겁니다.  
    \-WC는 좋지만, React팀에서는 React 컴포넌트를 WC로 대체하는 게 좋다고 확신은 못 합니다. 사람들은 가상돔을 제거할 수 있다고들 합니다. 그러나 캡슐화 뿐만 아니라 메모이제이션, 변경사항 계산, 스케줄링 등에 사용하죠. WC와 가상돔은 직교해요. SKateJS는 커스텀 요소에 가상돔을 사용하고 있어요.
    
*   웹어셈블리는 프레임워크에 어떤 영향을 미칩니까? : 그것은 JS를 우선시합니다. 성능적으로 중요한 부분을 위해서 polyfill로 사용할 것입니다.
    

* * *

  
번역하고 나니 번역기 돌린 것 같아서 계속 업데이트 할게요  
원본: ([https://redfin.engineering/i-watched-all-of-the-chrome-dev-summit-2017-videos-so-you-dont-have-to-9b62a593c3cb](https://redfin.engineering/i-watched-all-of-the-chrome-dev-summit-2017-videos-so-you-dont-have-to-9b62a593c3cb))