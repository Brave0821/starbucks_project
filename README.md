## BEM 작명법 
```
<div class="container">
    <div class="name"></div>
    <div class="item">
        <div class="name"></div>
    </div>
</div>

* 적용 후 

<div class="container">
    <div class="container__name"></div>
    <div class="item">
        <div class="item__name"></div>
    </div>
</div>

* 어느 부분의 일부분이다 알 수 있음.
```
```
<div class="btn primary"></div>
<div class="btn success"></div>
<div class="btn error"></div>


* 적용 후 

<div class="btn btn--primary"></div>
<div class="btn btn--success"></div>
<div class="btn btn--error"></div>
```

--------------------------------------------------------------------------------------------
## HTML 특수 문자표 

```
 <!-- <span class="this-year"> -> JS 활용해서 자동으로 현재 날짜로 수정됨. -->
    &copy; <span class="this-year"></span> Starbucks Coffee Company. All Rights Reserved.
```
html entities  -> html특수문자표   
https://www.w3schools.com/html/html_entities.asp
-->



-------------------------------------------------------------------------
## 사용한 라이브러리 정리

```
ScrollMagic: 주로 스크롤 이벤트를 기반으로 애니메이션과 이벤트 트리거를 관리하는 라이브러리.
Lodash: 데이터 조작 및 유틸리티 함수를 제공하는 범용 JavaScript 라이브러리.
GSAP: 고성능, 정밀한 제어가 가능한 애니메이션을 구현하는 데 특화된 라이브러리.

```

## JS lodash.js CDN

* https://cdnjs.com/libraries/lodash.js
Lodash : 사용시 lodash 라이브러리 사용할 때 js보다 위에 선언

```
window.addEventListener("scroll", _.throttle(function (){
    console.log("scroll!")
}, 300));
```
_.throttle - > 일정시간 한 번씩 실행되도록 제한을 걸다.

_.throttle(함수, 시간)

스크롤 이벤트시 많이 사용되니까 참고.

Why? 스크롤 할 때마다 여기에 연결되어져 있는 익명의 함수가 굉장히 많은 횟수에 걸쳐서 실행되기 때문에.
사용해주는게 좋다.


console.log(window.scrollY); 주면서 내릴 때 몇 픽셀 지점인지 확인가능.

----------------------------------------------------------------------------------------------

## JS gsap cdn

* https://cdnjs.com/libraries/gsap

### 애니메이션을 처리해주는 라이브러리 많이 사용한다.

* 예시 - > 오른쪽 뱃지가 서서히 사라지고 올리면 나타난다.
```
window.addEventListener("scroll", _.throttle(function (){
    console.log(window.scrollY);
    /* y가 500보다 커지면 */
    if (window.scrollY > 500) {
        // 배지 숨기기
        // gsap.to(요소, 지속시간, 옵션);
        gsap.to(badgeEl, .6, {
            /* name: '', */
            opacity: 0,
            display: "none"
        });
        /* 0.6초에 걸쳐서 서서히 사라진다.  */
    } else {
        // 배지 보이기
        gsap.to(badgeEl, .6, {
            /* name: '', */
            opacity: 1,
            display: "block"
        });
                /* 0.6초에 걸쳐서 서서히 보여진다..  */
    }
}, 300));
```

* gsap 위로 올려주는 cdn
 스크롤 기능.
 
```
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/ScrollToPlugin.min.js" integrity="sha512-1PKqXBz2ju2JcAerHKL0ldg0PT/1vr3LghYAtc59+9xy8e19QEtaNUyt1gprouyWnpOPqNJjL4gXMRMEpHYyLQ==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
```



----------------------------------------------------------------------------------------------
visual 부분 필기 
- section = 계층이다. 



###  FADE-IN: 순차적으로 나타나는 기능.
* 배너 오트밀, 카라멜 스푼 등등 순차적으로 나타냄


```
const fadeEls = document.querySelectorAll(".visual .fade-in");
/* fadeEl -> 요소부분은 내가 원하는 이름으로, 반복횟수 인덱스 */
fadeEls.forEach(function (fadeEl, index) {
    /* 2개의 매개변수를 가지고 있는 함수들이 반복적으로 실행 될 때 */
    gsap.to(fadeEl, 1, {
        delay:(index + 1) * 0.7,
        /*    delay:(index + 1) * 0.7, - > 
        0에 숫자 1 더해서 0.7 곱하면 fade-in 이라는 클래스를 가진 요소는 0.7초 후에 애니메이션 동작
        두 번쨰는 1.4초 세 번쨰 2.1  네 번쨰 2.7 뒤에 요소에 opacity 1로 나타내게 만듬.
        */
        opacity: 1
    } );
       // gsap.to(여기에선 반복요소, 지속시간 초 단위, 옵션);
    /* gsap.to - > 애니메이션 라이브러리 */
});
```
--------------------------------------------------------------------------------------------------

## 기타 도움되는 

* reset css
```
   <link href="https://cdn.jsdelivr.net/npm/reset-css@5.0.2/reset.min.css" rel="stylesheet">
    <!-- https://www.jsdelivr.com/package/npm/reset-css 리셋 css 추가. -->
```

* 아이콘 

```
    <!-- https://fontawesome.com/search?q=Search&o=r 아이콘 -->
    <!-- https://fonts.google.com/icons -->
    <link rel="stylesheet" href="https://fonts.googleapis.com/icon?family=Material+Icons" />
```
### 사용법 : ^ 에 아이콘 사이트에 들어가서 원하는 아이콘 네임 가져와서 밑에 입력
```
 ex) <div class="material-icons">add_circle</div>

```

### a태그에 #보단 <a href="javascript:void(0)"></a> 사용권장

### CSS calc 사용해서 자동으로 넓이 계산.

```
.notice .promotion .swiper {
    /* 총 넓이에 819 이미지 3장이 들어가고 사이사이 공간 10px 즉 2개니까 20px*/
    width: calc(819px * 3 + 20px);
}
```
### 스크롤 시 화면 고정 위에 요소만 움직이게

* background-attachment: fixed;
```
.pick-your-favorite {
    background-image: url("../images/favorite_bg.jpg");
    background-repeat: no-repeat;
    background-position: center;
    /* 요소가 스크롤될때 같이 스크롤안되고 고정됨 즉 화면은 붙어있고 위에 요소는 스크롤에 움직임. 딱 보면 알거임*/
    background-attachment: fixed;
    /* 배경 이미지를 요소에 더 넓은 너비에 출력 */
    background-size: cover;
}

```
### 줄바꿈이 가능하게 

*   /* flex-wrap: wrap;: 글이 넘치면 줄바꿈이 가능한 형태로 만들어줌 */

```
.pick-your-favorite .text-group {
    background-color: tomato;
    display: flex;
    width: 362px;
    /* flex-wrap: wrap;: 줄바꿈이 가능한 형태로 만들어줌 */
    flex-wrap: wrap;
}
```

### css로 버튼 호버 시 변환시키게 

```
/* btn WHITE */
.btn.btn--white {
    color: #fff;
    border-color: #fff;
}
.btn.btn--white:hover {
    color: #333;
    background-color: #fff;
}

```

---------------------------------------------------------------------------------------------------
# swiperjs v11.1.1 버젼

* https://swiperjs.com/


```

 <!-- 스와이퍼 CDN -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.css"/>
    <script src="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.js"></script>
    <script defer src="./js/main.js"></script>

```    
MAIN.JS 위에 CDN

/* active -> 활성화 */


.swiper-pagination-bullet에 효과주기

```
.notice .promotion .swiper-pagination .swiper-pagination-bullet {
    background-color: transparent; /* 투명한색 */
    background-image: url("../images/promotion_slide_pager.png");
    width: 12px; height: 12px;
    margin-right: 6px;
    outline: none;
}

.notice .promotion .swiper-pagination .swiper-pagination-bullet:last-child {
    margin-right: 0;
}

/* 활성화된 페이지 번호 */
.notice .promotion .swiper-pagination .swiper-pagination-bullet-active {
    background-image: url("../images/promotion_slide_pager_on.png");
}

/* 다중선택자. */
.notice .promotion .swiper-button-prev,
.notice .promotion .swiper-button-next {
    width: 42px; height: 42px;
    border: 2px solid #333;
    border-radius: 50%;
    position: absolute;
    top: 300px; z-index: 1;
    cursor: pointer;
    outline: none;
}

```

* 스와이퍼 next, prev 기본 양식 제거 

```
.notice .promotion .swiper-button-prev::after{
    display: none;
}
```


# YOUTUBE api 적용 

```
// 2. This code loads the IFrame Player API code asynchronously.
/* const 변수 생성부분 
createElement 요소 생성 메소드
*/
const tag = document.createElement('script');

tag.src = "https://www.youtube.com/iframe_api";
/* src에 외부 js 라이브러리가 할당됨. */
var firstScriptTag = document.getElementsByTagName('script')[0];
firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);

// 3. This function creates an <iframe> (and YouTube player)
//    after the API code downloads.
/* var player; */
/* onYouTubeIframeAPIReady() 변경x api가 찾을 수 있게 */
function onYouTubeIframeAPIReady() {
    /* HTML에 <div id="player"></div> 아이디 값 찾아서 알아서 적용 */
        new YT.Player('player', {
     /*    height: '360',
        width: '640', */
        /* 어떤 ID값을 가지는 유튜브 영상을 출력할거냐. 
         videoId: 'M7lc1UVf-VE',

         /* https://www.youtube.com/watch?v=An6LvWQuj_8 
         여기중에 An6LvWQuj_8 이 부분이 ID값이고 제어를 위해 필요하다.
         */
        // videoId: 'M7lc1UVf-VE',
        videoId: 'An6LvWQuj_8', /* 최초 재생할 유튜브 영상 ID */
        playerVars : {
            autoplay : true , // 자동 재생 유무
            loop: true, // 반복 재생 유무 ture일땐 밑에 재공해야함.
            videoId: 'An6LvWQuj_8', // 반복 재생할 유튜브 영상 id 목록
        },
        events: {
            /*  onReady 준비가 되면 함수 실행 
            event 매개변수의 이름으로 받아서 함수 내부에서 사용가능
            */
            onReady: function (event) {
                /* 타켓 : 재생되는 영상 */
                event.target.mute() // 음소거
            }
        }
        /* events: {
            'onReady': onPlayerReady,
            'onStateChange': onPlayerStateChange
        } */
    });
}

```
* html 부분
```
    <!-- YUPTUBE VIDEO -->
    <section class="youtube">
    <div class="youtube__area">
        <!-- player 실제 유튜브가 실행되는 장소 -->
        <div id="player"></div>
    </div>
    <div class="youtube__cover">
        
    </div>
    </section>
```

* css 부분
```
.youtube {
    position: relative;
    height: 700px;
    background-color: #333;
    overflow: hidden;
}

.youtube .youtube__area {
    width: 1920px;
    background-color: tomato;
    position: absolute;
    left: 50%;
    /* 정중앙으로 보내기 */
    margin-left: calc(1920px / -2);
    top: 50%;
    margin-top: calc(1920px * 9 / 16 / -2);

}
/* 가상요소선택자 ::before */
.youtube .youtube__area::before {
    content: "";
    display: block;
    width: 100%;
    height: 0;
    /* 16:9 박스 만들기 밑에  padding-top: 56.25%;*/
    padding-top: 56.25%;
}
.youtube .youtube__cover {
    background-image: url("../images/video_cover_pattern.png");
    background-color: rgba(0,0,0,0.3);
    position: absolute;
    top: 0; left: 0;
    width: 100%;
    height: 100%;
}

```


# 유튜브 위 floating 애니메이션 

* https://gsap.com/docs/v3/Eases/


```
/* youtube 애니메이션과 연관된.  */
// 범위 랜덤 함수(소수점 2자리까지)
function random(min, max) {
    // `.toFixed()`를 통해 반환된 문자 데이터를,
    // `parseFloat()`을 통해 소수점을 가지는 숫자 데이터로 변환
    return parseFloat((Math.random() * (max - min) + min).toFixed(2))
}

/* youtube.js 위에 애니메이션 */
/* size : 위 아래로 움직이는 범위 */
function floatingObject(selector, delay, size) {
    // gsap.to(요소, 지속시간, 옵션);
    /* 위에 random 함수 할당. */
    gsap.to(selector, // 선택자
        random(1.5, 2.5), // 애니메이션 동작 시간
        { // 옵션
        y: size, /* size 매개변수 할당 */
        /* repeat: -1, 무한반복 */
        repeat: -1,
        /* yoyo 한번 재생된 애니메이션을 뒤로 재생하게해줌. */
        yoyo: true,
        /* gsap easing */
        ease: "power1.inOut",
        delay: random(0, delay)
        }
    );
}
floatingObject(".floating1", 1, 15);
floatingObject(".floating2", 0.5, 15);
floatingObject(".floating3", 1.5, 20);
```
----------------------------------------------------

# <!-- ScrollMagic cdn추가 -->

ScrollMagic를 사용하면 


```
    <script src="https://cdnjs.cloudflare.com/ajax/libs/ScrollMagic/2.0.8/ScrollMagic.min.js" integrity="sha512-8E3KZoPoZCD+1dgfqhPbejQBnQfBXe8FuwL4z/c8sTrgeDMFEnoyTlH3obB4/fV+6Sg0a0XF+L/6xS4Xx1fUEg==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
```
* 예시1 
delay-1를 붙여서 전환효과 효과를 0.x초 지연시킬 수 있다.

```
    <!-- SEASON PRODUCT 0529 scroll-spy 추가-->
    <section class="season-product scroll-spy">
        <div class="inner">
            <img src="./images/floating3.png" alt="icon" class="floating floating3" />
            <img src="./images/season_product_image.png" alt="" class="product back-to-position to-right delay-0" />
            <div class="text-group">
                <img src="./images/season_product_text1.png" alt="" class="title back-to-position to-left delay-1" />
                <img src="./images/season_product_text2.png" alt="" class="description back-to-position to-left delay-2" />
                <div class="more back-to-position to-left delay-3">
                    <a href="javascript:void(0)" class="btn">자세히 보기</a>
                </div>
            </div>

        </div>
    </section>

```



```
const spyEls = document.querySelectorAll("section.scroll-spy");
/*scroll-spy 추가 spyEls s 반복이니 forEach 사용가능 */
spyEls.forEach(function (spyEl){
    /* 지정한다 클래스 속성을 토글(넣었다 뺏다.)  */
    new scrollMagic
    .Scene({
        triggerElement: spyEl, // 보여짐 여부를 감시할 요소를 지정
        triggerHook: .8 //0.8 부분에 걸리면 실행됨
    })
    .setClassToggle(spyEl, "show")
    .addTo(new scrollMagic.Controller());
})

 ```
scroll-spy를 가진 클래스들을 지속적으로 감시 
요소가 지정된 곳을 넘어 보이는 순간 show 클래스를 보여준다.

```
/* 스크롤 이벤트  */
.back-to-position {
    opacity: 0;
    transition: 1s;
}

.back-to-position.to-right {
    transform: translateX(-150px);
}

.back-to-position.to-left {
    transform: translateX(150px);
}

.show .back-to-position {
    opacity: 1;
    /* transform: translateX(0); 원래 위치로 돌아옴 */
    transform: translateX(0);
}

.show .back-to-position.delay-0 {
    /* 전환효과 효과를 0.x초 지연시킨다는 의미 */
    transition-delay: 0s;
}

.show .back-to-position.delay-1 {
    transition-delay: .3s;
}

.show .back-to-position.delay-2 {
    transition-delay: .6s;
}

.show .back-to-position.delay-3 {
    transition-delay: .9s;
}
```