---
title: Building a Modern Media Experience (Chrome Dev Summit 2017) from Chrome Media Team
tags:
  - 번역
  - 동영상
date: 2017-11-03 11:11:11
---
[](#Chrome-dev-summit-2017 "Chrome dev summit 2017")Chrome dev summit 2017
==========================================================================

[](#Building-a-Modern-Media-Experience-Chrome-Dev-Summit-2017-from-Chrome-Media-Team "Building a Modern Media Experience (Chrome Dev Summit 2017) from Chrome Media Team")Building a Modern Media Experience (Chrome Dev Summit 2017) from Chrome Media Team
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

> 해당 포스트는 지난 chrome dev summit 2017 중 크롬브라우저에서의 미디어 재생에 관한 내용을 러프하게 옮긴 것입니다. 지적 참견 환영합니다

원본 영상을 보시려면 아래 링크로

### [](#Intro "Intro")Intro

미디어 전달의 중요성이 점차 높아지고 있음:

*   Forbes, iHeartRadio, Geo Cinema 등의 사이트에서 동영상을 주요하게 활용중
*   모바일 웹 미디어의 시청 시간 증가  
    : 지난 6개월간 크롬 안드로이드에서 사용자별 미디어 재생 시간이 2배 증가함

### [](#목차 "목차")목차

*   미디어 관련 크롬 업데이트 사항
*   조금 더 발전된 미디어 적용 사례
*   PWA([참고](http://terms.naver.com/entry.nhn?docId=3581225&cid=59088&categoryId=59096)) 활용 사례와 offline 미디어 재생사례 소개

#### [](#1-크롬-업데이트-사항 "1. 크롬 업데이트 사항")1\. 크롬 업데이트 사항

*   오토플레이

문제점 1. 오디오재생이 사용자의 의지와 상관없이 일어나는 것은 가장 많은 불만 사례이다.

문제점 2. 데스크탑과 모바일간에 오토플레이 정책이 일관적이지 않음

\-> 바뀐 정책:

모든 플랫폼에서(iframe포함) 음소거된 미디어 자동재생만이 허용됨

세 가지 경우만 빼고

*   사용자 액션이 있을때: 미디어 탭 또는 클릭, 동영상 페이지로 이동
*   데스크탑에서 사용자가 오디오를 많이 사용할 때
*   모바일 환경에서 사이트가 홈화면에 추가되었을 때

\-promise로 사용자 환경에서의 음소거 자동재생 허용여부 확인 가능  

```javascript

var promise = document.querySelector('video').play()

  if (promise !== undefined) {

    promise.then(\_ => {

    // 오토플레이 스타트

    }).catch(error => {

      // 오토플레이가 허용되지 않음

      // 풀래아버튼이 노출되고, 사용자가 클릭하면 재생

    })

  }
```

\-iframe 내부의 미디어 경우 앞으로 attribute를 통해 액세스 권한을 부여할 수 있음  

<iframe width="560" height="315" src="https://www.youtube.com/embed/WRSEJCKu7zA" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

\-web btt 및 ttml의 렌더링을 사용자 정의할 수 있음

\-오프라인으로 보호되는 미디어재생이 허용

#### [](#2-더-나은-미디어-적용-사례 "2. 더 나은 미디어 적용 사례")2\. 더 나은 미디어 적용 사례

\-2초간 버퍼링이 있을 때 초당 약 6%가 재생하지 않음

*   preload를 통해 미디어 재생을 빨리 처리할 수 있음

*   preload를 auto로 하면 인앱 데이터가 캐싱되고 버퍼링 중지 없이 전체 재생이 가능..
    
    ```javascript
    
    <video id="video" preload="auto" src="file.mp4" controls></video>
    
    <script>
    
         video.addEventListener('loadedmetadata', function () {
    
              var bufferedSeconds = video.buffered.end(0) - video.buffered.start(0)
    
              console.log(bufferedSeconds + ' seconds of video are ready to play')
    
            })
    
    </script>
    
```

하지만 브라우저가 이를 무시할 수 있다(ex.데이터 세이버 사용)

*   link preload는 페이지가 다운로드 중일 때 윈도우 로드를 직접 차단하지 않고 브라우저가 자원에 대한 요청을 하도록 하는 기능임.

–link preload된 리소스는 브라우저에 로컬로 저장되며 DOM, javascript나 css 에서 사용될 때까지 비활성화됨

*   MSC API를 활용한 예제

```javascript

<link rel="preload" as="fetch" href="https://cdn.com/file.webm">

<video id="video" controls></video>

<script>

    const mediaSource = new MediaSource()

    video.src = URL.createObjectURL(mediaSource)

    mediaSource.addEventListener('sourceopen', async function() {

      const sourceBuffer = mediaSource.addSourceBuffer('video/webm; codecs=vp9')

      const res = await fetch('https://cdn.com/file.webm')

      const data = await res.arrayBuffer()

      sourceBuffer.appendBuffer(data)

    })

</script>

```

\-디바이스 메모리가 1기가 미만인 경우 사용자가 저성능 장치에 있다고 가정함(http 헤더 체크)  
사용자가 데이터 요금을 지불해야 할 수 있음을 명심

미디어 세션 api사용: 브라우저에서 이를 지원하는 경우 제목, 아티스트 같은 메타 데이터를 제공 가능

```javascript


// 미디어가 재생될 때

if ('mediaSession' in navigator ) {

  navigator.mediaSession.metadata = new MediaMetadata({

    title: 'Never Gonna Give You Up',

    artist: 'Rick Astley',

    album: 'Whenever You Need Somebody',

    artwork: \[

      { src: 'https://..', sizes: '256x256', type: 'image/png' },

      { src: 'https://..', sizes: '256x256', type: 'image/png' }

    \]

  })

}

```

비디오가 보이지 않을 때 비디오 재생 멈추기  

```javascript

// 미디어가 재생될 때

document.addEventListener('visivilitychange', function () {

  if (document.visibilityState === 'hidden') {

    video.pause()

  }

})
```

디바이스가 가로 모드일 때 풀스크린으로 세팅하기  


```javascript

screen.orientation.addEventListener('change', function() {

      if (screen.orientation.type.startWith('landscape')) {

        video.requestFullscreen()

      } else if (document.fullscreenElement) {

        document.exitFullscreen()

      }

    })

```

유용한 API들  

```javascript

// 미디어 액션 핸들러

navigator.mediaSession.setActionHandler('seekbackward', evt => { ... })

navigator.mediaSession.setActionHandler('seekforward', evt => { ... })

navigator.mediaSession.setActionHandler('play', evt => { ... })

navigator.mediaSession.setActionHandler('pause', evt => { ... })

navigator.mediaSession.setActionHandler('nexttrack', evt => { ... })

navigator.mediaSession.setActionHandler('previoustrack', evt => { ... })

// UI를 알림 컨트롤과 동기화

// 미디어가 로드되었으나 아직 플레이되지 않고 있을 때 유용한 코드

navigator.mediaSession.playbackState = 'playing'
```


#### [](#3-voot-com-사례 "3. voot.com 사례")3\. voot.com 사례

\-인도는 2천 6백만대가 저성능 디바이스를 사용

*   인터넷이 될 때 다운로드해서 오프라인 모드에서 미디어를 재생할 수 있음
*   Index db를 삽입하여 다운로드한 리소스에 대한 기록을 남김  
    \-> 백그라운드를 불러온 리소스와 비교하여 현재 미디어를 확인 -> 다운로드한 리소스를 캐시에 저장

인도의 경우 데이터 환경이 안정적이지 않음  
버스에서 vootGo에 로그인하여 wifi를 이용, 컨텐츠를 다운받을 수 있게 함