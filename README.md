# Hyperledger-study-48

하이퍼레져 앱 만들기 실습 48일차 - 이미지 슬라이드

1. 자바와 css로 이미지 슬라이더 구성 - index.html

        <!DOCTYPE html>
        <html>
        <head>
             <meta charset="utf-8">
             <title>Javascript Example</title>
             <style type="text/css">
                 body{
                     font-size: .8em;
                     text-align: center;   
                     margin: 0; padding: 0;
                 }
                 .slider{
                     width: 100%;
                     position: relative;
                 }
                 .slider_item{
                     width: 100%;
                     height: 500px;
                     overflow: hidden;
                     position: absolute;
                     z-index: 0;
                     opacity: 0;
                     transition: all .7s ease-in-out;
                     transform: scale(.8);
                 }
                 img {width: 100%;}

                .showing{
                     opacity: 1;
                     z-index: 1;
                     transform: none;
                 }
             </style>
        </head>
        <body>
             <h1>Javascript Example 001 - 자동 슬라이더</h1>
             <p>자바스크립트와 CSS만으로 Carousel Slider 효과를 구현해 봅니다. </p>

            <!-- Slider -->
             <div class="slider">
                 <!-- items -->
                 <div class="slider_item"><img src="home.png"></div>
                 <div class="slider_item"><img src="create.jpg"></div>
                 <div class="slider_item"><img src="query.jpg"></div>
                 <div class="slider_item"><img src="change.jpg"></div>
             </div>

            <script type="text/javascript">
                 const showing_class = "showing";
                 const firstSlide = document.querySelector(".slider_item:first-child");
                 function slide(){
                     const currentSlide = document.querySelector(`.${showing_class}`); // showing 클래스가  있는 엘리먼트를 찾는다.
                     if(currentSlide){
                         // 지금 shwoing 클래스를 가진 엘리먼트 다음 엘리먼트에 클래스를 추가 한다.
                         currentSlide.classList.remove(showing_class);
                         const nextSlide = currentSlide.nextElementSibling;
                         // 다음 엘리먼트가 있는지 없는지 체크 후 처리
                         if (nextSlide){
                             console.log(currentSlide);
                             nextSlide.classList.add(showing_class);
                         } else {//마지막이면(그다음 형제 엘리먼트가 없으니까) 첫 슬라이드에 추가 함.
                             firstSlide.classList.add(showing_class);
                         }

                    } else { // showing 클래스가 지정된 엘리먼트가 없으면 첫번째에 추가해 준다.(페이지 시작시)
                         firstSlide.classList.add(showing_class);
                     }
                 }

                slide();
                 setInterval(slide, 3000); // 1000은 1초

             </script>

        </body>
        </html>

2. css로 이미지 슬라이드 구성 - index2.html

        <!DOCTYPE html>
        <html lang="en">
        <head>
        <meta charset="UTF-8">
        <title>Document</title>
        </head>
        <body>
        <style>
          *{margin:0;padding:0;}
          ul,li{list-style:none;}
          #slide{height:300px;position:relative;overflow:hidden;}
          #slide ul{width:400%;height:100%;transition:1s;}
          #slide ul:after{content:"";display:block;clear:both;}
          #slide li{float:left;width:25%;height:100%;}
          #slide input{display:none;}
          #slide label{display:inline-block;vertical-align:middle;width:10px;height:10px;border:2px solid #666;background:#fff;transition:0.3s;border-radius:50%;cursor:pointer;}
          #slide .pos{text-align:center;position:absolute;bottom:10px;left:0;width:100%;text-align:center;}
          #pos1:checked~ul{margin-left:0%;}
          #pos2:checked~ul{margin-left:-100%;}
          #pos3:checked~ul{margin-left:-200%;}
          #pos4:checked~ul{margin-left:-300%;}
          #pos1:checked~.pos>label:nth-child(1){background:#666;}
          #pos2:checked~.pos>label:nth-child(2){background:#666;}
          #pos3:checked~.pos>label:nth-child(3){background:#666;}
          #pos4:checked~.pos>label:nth-child(4){background:#666;}
        </style>
        <div id="slide">
          <input type="radio" name="pos" id="pos1" checked>
          <input type="radio" name="pos" id="pos2">
          <input type="radio" name="pos" id="pos3">
          <input type="radio" name="pos" id="pos4">
          <ul>
            <li><img src="home.png"></li>
            <li><img src="query.jpg"></li>
            <li><img src="create.jpg"></li>
            <li><img src="change.jpg"></li>
          </ul>
          <p class="pos">
            <label for="pos1"></label>
            <label for="pos2"></label>
            <label for="pos3"></label>
            <label for="pos4"></label>
          </p>
        </div>
        </body>
        </html>

3. css로 이미지 슬라이드 구성2 - index3.html

        <!DOCTYPE html>
        <html>
        <head>
            <meta charset="UTF-8">
            <title>LightSlider Test</title>
            <link rel="stylesheet"  href="https://han3283.cafe24.com/js/lightslider/css/lightslider.css"/>
            <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js"></script>
            <script src="https://han3283.cafe24.com/js/lightslider/js/lightslider.js"></script>
        </head>

        <body>
            <div class="slide-wrap">
                <div class="slide-content">
                    <ul id="slider" class="slider">
                        <li class="item1">
                            <h3>사과</h3>
                        </li>
                        <li class="item2">
                            <h3>체리</h3>
                        </li>
                        <li class="item3">
                            <h3>딸기</h3>
                        </li>
                        <li class="item4">
                            <h3>포도</h3>
                        </li>
                        <li class="item5">
                            <h3>레몬</h3>
                        </li>
                        <li class="item6">
                            <h3>자몽</h3>
                        </li>
                    </ul>
                </div>
            </div>
            <style>
              ul{
                list-style: none outside none;
                padding-left: 0;
                margin: 0;
              }
              .slide-content .slide-content{
                margin-bottom: 60px;
              }
              .slider li{
                text-align: center;
                color: #FFF;
                background-size:cover;
                background-position: center;
              }
              .slider h3 {
                margin: 0;
                padding: 100px 0;
                height:250px;
              }
              .slide-content{
                width: 100%;
                height:300px;
              }
              .item1{background-image:url('http://han3283.cafe24.com/images/apple.jpg');}
              .item2{background-image:url('http://han3283.cafe24.com/images/cherry.jpg');}
              .item3{background-image:url('http://han3283.cafe24.com/images/strawberry.jpg');}
              .item4{background-image:url('http://han3283.cafe24.com/images/grape.jpg');}
              .item5{background-image:url('http://han3283.cafe24.com/images/lemon.jpg');}
              .item6{background-image:url('http://han3283.cafe24.com/images/grapefruit.jpg');}
            </style>
        </body>
        </html>
        <script>
          $(document).ready(function() {
            $("#slider").lightSlider({
                mode:'slide',    // 이미지가 표시되는 형식 (fade / slide)
                loop:true,       // 무한반복 할 것인지
                auto:true,       // 자동 슬라이드
                keyPress:true,   // 키보드 탐색 허용
                pager:false,     // 페이지 표시
                speed:1500,      // 슬라이드 되는 속도
                pause:3000       // 이미지가 머무는 시간
            });
          });
        </script>

4. Jquery와 css로 이미지 슬라이드 구성 - index4.html

        <!DOCTYPE html>
        <html>
        <head>
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
        </head>
        <body>
        <style>
        * {
          margin: 0px;
          padding: 0px;
        }

        ul,
        ol,
        li {
          list-style: none;
        }

        a {
          text-decoration: none;
        }

        img {
          vertical-align: top;
          border: none;
        }

        .slide {
          position: relative;
          padding-top: 50px;
          overflow: hidden;
        }

        .panel {
          width: 400%;
        }

        .panel:after {
          content: "";
          display: block;
          clear: both;
        }

        .panel>li {
          width: 25%;
          height: 200px;
          float: left;
          background-repeat: no-repeat;
          background-size: 100% 100%;
          position: relative;
        }

        .panel>li:nth-of-type(1) {
          background-image: url('home.png');
        }

        .panel>li:nth-of-type(2) {
          background-image: url('query.jpg');
        }

        .panel>li:nth-of-type(3) {
          background-image: url('create.jpg');
        }

        .panel>li:nth-of-type(4) {
          background-image: url('change.jpg');
        }

        .dot:after {
          content: "";
          display: block;
          clear: both;
        }

        .dot {
          position: absolute;
          left: 50%;
          bottom: 10%;
          transform: translateX(-50%);
        }

        .dot>li {
          float: left;
          width: 25px;
          height: 25px;
          border-radius: 50%;
          background-color: #fff;
          margin-left: 10px;
          margin-right: 10px;
          text-indent: -9999px;
          cursor: pointer;
        }

        .dot>li.on {
          background-color: #342f2f;
        }

        .prev {
          position: absolute;
          width: 64px;
          height: 64px;
          background-image: url('left-arrows.png');
          top: 60%;
          transform: translateY(-50%);
          left: 10%;
          cursor: pointer;
        }

        .next {
          position: absolute;
          width: 64px;
          height: 64px;
          background-image: url('right-arrows.png');
          top: 60%;
          transform: translateY(-50%);
          right: 10%;
          cursor: pointer;
        }  
        </style>
        <div class="slide">
          <ul class="panel">
            <li>1번슬라이드</li>
            <li>2번슬라이드</li>
            <li>3번슬라이드</li>
            <li>4번슬라이드</li>
          </ul>
          <ul class="dot">
            <li class="on">슬라이드 버튼1번</li>
            <li>슬라이드 버튼2번</li>
            <li>슬라이드 버튼3번</li>
            <li>슬라이드 버튼4번</li>
          </ul>
          <div class="prev"></div>
          <div class="next"></div>
        </div>
        </body>
        </html>
        <script>
        $(document).ready(function() {
          slide();
        });


        // 슬라이드 
        function slide() {
          var wid = 0;
          var now_num = 0;
          var slide_length = 0;
          var auto = null;
          var $dotli = $('.dot>li');
          var $panel = $('.panel');
          var $panelLi = $panel.children('li');

          // 변수 초기화
          function init() {
            wid = $('.slide').width();
            now_num = $('.dot>li.on').index();
            slide_length = $dotli.length;
          }

          // 이벤트 묶음
          function slideEvent() {

            // 슬라이드 하단 dot버튼 클릭했을때
            $dotli.click(function() {
              now_num = $(this).index();
              slideMove();
            });

            // 이후 버튼 클릭했을때
            $('.next').click(function() {
              nextChkPlay();
            });

            // 이전 버튼 클릭했을때
            $('.prev').click(function() {
              prevChkPlay();
            });

            // 오토플레이
            autoPlay();

            // 오토플레이 멈춤
            autoPlayStop();

            // 오토플레이 재시작
            autoPlayRestart();

            // 화면크기 재설정 되었을때
            resize();
          }

          // 자동실행 함수
          function autoPlay() {
            auto = setInterval(function() {
              nextChkPlay();
            }, 3000);
          }

          // 자동실행 멈춤
          function autoPlayStop() {
            $panelLi.mouseenter(function() {
              clearInterval(auto);
            });
          }


          // 자동실행 멈췄다가 재실행
          function autoPlayRestart() {
            $panelLi.mouseleave(function() {
              auto = setInterval(function() {
                nextChkPlay();
              }, 3000);
            });
          }

          // 이전 버튼 클릭시 조건 검사후 슬라이드 무브
          function prevChkPlay() {
            if (now_num == 0) {
              now_num = slide_length - 1;
            } else {
              now_num--;
            }
            slideMove();
          }

          // 이후 버튼 클릭시 조건 검사후 슬라이드 무브
          function nextChkPlay() {
            if (now_num == slide_length - 1) {
              now_num = 0;
            } else {
              now_num++;
            }
            slideMove();
          }

          // 슬라이드 무브
          function slideMove() {
            $panel.stop().animate({
              'margin-left': -wid * now_num
            });
            $dotli.removeClass('on');
            $dotli.eq(now_num).addClass('on');
          }

          // 화면크기 조정시 화면 재설정
          function resize() {
            $(window).resize(function() {
              init();
              $panel.css({
                'margin-left': -wid * now_num
              });
            });
          }
          init();
          slideEvent();
        }
        </script>

5. javascript로 이미지슬라이드 구성 - index5.html

        <!DOCTYPE html>
        <html lang="en">
          <head>
            <meta charset="UTF-8">
            <title>Misae-Zero</title>
          </head>

          <script>
            var index = 0;
            window.onload = function(){
              slideShow();
            }
            function slideShow(){
              var i;
              var x = document.getElementsByClassName("slide1");
              for (i=0; i < x.length; i++){
                x[i].style.display = "none";
              }
              index++;
              if (index > x.length){
                index = 1;
              }
              x[index-1].style.display = "block";
              setTimeout(slideShow, 3000);
            }
          </script>

          <body>
            <div>
              <a href="https://naver.com"><img class="slide1" src="home.png"></a>
              <a href="https://daum.net"><img class="slide1" src="query.jpg"></a>
              <a href="https://google.com"><img class="slide1" src="create.jpg"></a>
              <a href="https://yahoo.com"><img class="slide1" src="change.jpg"></a>
            </div>
          </body>
        </html>

6. bxslider를 활용하여 이미지 슬라이드 만들기 - index7.html

        <html> 
        <head> 
            <meta charset="utf-8"> 
            <link rel="stylesheet" href="https://cdn.jsdelivr.net/bxslider/4.2.12/jquery.bxslider.css"> 
            <script src="https://code.jquery.com/jquery-1.11.3.js"></script> 
            <script src="https://cdn.jsdelivr.net/bxslider/4.2.12/jquery.bxslider.min.js"></script> 
            <script>
            var j = $.noConflict(true); 
            j(document).ready(function(){ 
                var main = j('.bxslider').bxSlider({ 
                mode: 'fade', 
                auto: true,	//자동으로 슬라이드 
                controls : true,	//좌우 화살표	
                autoControls: true,	//stop,play 
                pager:true,	//페이징 
                pause: 3000, 
                autoDelay: 0,	
                slideWidth: 800, //이미지 박스 크기설정
                speed: 500, 
                stopAutoOnclick:true,
                touchEnabled : (navigator.maxTouchPoints > 0),
            });

            j(".bx-stop").click(function(){	// 중지버튼 눌렀을때 
                main.stopAuto(); 
                j(".bx-stop").hide(); 
                j(".bx-start").show(); 
                return false; 
            }); 

            j(".bx-start").click(function(){	//시작버튼 눌렀을때 
                main.startAuto(); 
                j(".bx-start").hide(); 
                j(".bx-stop").show(); 
                return false; 
            }); 

            j(".bx-start").hide();	//onload시 시작버튼 숨김. 
            }); 
            </script> 
        </head> 

        <body> 
        <div class="home__slider"> 
            <div class="bxslider"> 
                <div class="image">
                    <a href="https://naver.com">
                    <img src="image1.jpg" alt="그림1" ti>
                    <div class="text">
                        <h1>Home</h1>
                    </div>
                    </a>
                </div>
                <div class="image">
                    <a href="https://naver.com">
                    <img src="image2.jpg" alt="그림2" ti>
                    <div class="text">
                        <h1>Query</h1>
                    </div>
                    </a>
                </div>
                <div class="image">
                    <a href="https://naver.com">
                    <img src="image3.jpg" alt="그림3" ti>
                    <div class="text">
                        <h1>Create</h1>
                    </div>
                    </a>
                </div>
                <div class="image">
                    <a href="https://naver.com">
                    <img src="image4.jpg" alt="그림4" ti>
                    <div class="text">
                        <h1>Change</h1>
                    </div>
                    </a>
                </div>
            </div> 
        </div>
        <style type="text/css">
            .image {
                position:relative;
                float:left; /* optional */
            }

            .image .text {
                position:absolute;
                top:20%; /* in conjunction with left property, decides the text position */
                left:35%;
                width:700px; /* optional, though better have one */
                font-size: 50;
                color: white;
            }
        </style>
        </body> 
        </html>
