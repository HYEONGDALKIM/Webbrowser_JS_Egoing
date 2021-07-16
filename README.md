# Webbrowser_JS_Egoing 
----------------------------------------------------------------------------------------------------------
##### - Sublime Text2, 구글 크롬 개발도구 
##### - JavaScript 는 WB, Node.js, GAS(호스트환경)를 제어하는 방법
##### - 파일 여는 방법 웹브라우에서 ctrl + O 누르고 디렉터리로 이동한 후 파일을 클릭.
##### - Sublime 에서 html 치고 TAB을 누르면 기본형식이 나온다. body안에 script를 만들때 도 마찬가지이다.
##### - HTML과 CSS는 정적인 언어이다.JS는 HTML과 CSS로 만들어진 웹페이지를 동적으로 변경해주는 언어이다. 
##### ㄴ 경고창을 띄우고, 탭인터페이스를 만들고, Drag & Drop 기능의 웹에플리케이션을 만들수 있다. 
##### - HTML5 부터는 script 뒤에 type = "text/javascript" 이 빠져도 된다.
-----------------------------------------------------------------------------------------------------------

## **HTML에서 JS 로드하기**

#### >> inline
     
onclick >> 클릭했을 때 JS코드가 브라우저에 의해서 실행 <이벤트>

ex) onclick="alert('Hello world')"
     
#### >> script
script까지는 HTML문법이고 script안에 내용을 자바스크립트로 해석해서 실행한다.

##### >> JS파일을 외부 파일로 분리
html 파일에서 다음과 같이 JS소스코드 위치경로를 잡아주고

<script src= "./script.js"></script> 
소스코드 위치경로,  <./ >현재파일과 같은 디렉토리 안에있는

JS 파일안에 html안에 있던 script부분의 JS부분만 분리해서 저장

분리한 것이 용량도 적게쓰고 더 효율적임, 유지보수가 편리함

##### >> Scirpt를 head태그에 위치가능하지만 오류가 발생한다

window.onload = function(){ 여기안에 넣어주면 에러가 사라진다. 

-----------------------------------------------------------------------------------------------------------
## **Object Model**

브라우저가 JS로 제어할 수 있도록 브라우저의 여러구성요소들을 객체로 만들어서 제공해주는 것이다.d

document.getElementsByTagName('img'); // img태그의 이름을 가지는 elements를 가지고 와서 리턴한다.

여러개의 값을 가질려면 JS에서는 return 값으로 배열을 사용하면 된다. imgs, imgs[0]

//imgs[0].style.width='300px'; 이미지의 CSS부분의 크기를 300px로 잡는다//

(출처 : http://learn.javascript.ru/browser-environment)

![image](https://user-images.githubusercontent.com/78002734/125192058-baa50400-e280-11eb-95ce-dca671fbabf0.png)

window는 전역객체, window, frame  //   가장 중요한 것은 property : document 

window.document , documnet  정확하게 같은 의미가 된다. 

Document 는 DOM - (Document object model) 을 가진다. 

BOM - Browser object model // navigator, screen, location, frames, historym XMLHttpRequest

JavaScript Core // Object, Array, Function

-----------------------------------------------------------------------------------------------------------
## **BOM** 

Browser Object Model 

#### >> 전역객체 Window

함수에 속해 있지않으면 모두 window 안에 있는 것 이므로 window.a 나 a 나 같음

#### >> 사용자와 커뮤니케이션 하기

**alert** - 경고창, 사용자에게 정보제공, 디버깅등의 용도
![image](https://user-images.githubusercontent.com/78002734/125197190-a9b3bd00-e297-11eb-91c1-38865abf527b.png)

최근에는 console.log 를 많이 써서 디버깅의 용도로는 잘 쓰지 않는다.

**confirm** -  확인을 누르면 true, 취소를 누르면 false를 리턴한다.
![image](https://user-images.githubusercontent.com/78002734/125197164-94d72980-e297-11eb-9300-aa2671f02531.png)

**prompt** - 사용자가 입력한 값을 받아서 JS가 얻어 낼 수 있는 기능 

![image](https://user-images.githubusercontent.com/78002734/125197155-8db01b80-e297-11eb-9a1b-ef40c3f8af21.png)

#### >> Location 객체

- 현재 윈도우의 URL을 알려주는 객체

console.log(location.toString(), location.href); 

console.log(location)

alert(location) = alert(location.toString());

- URL Parsing
location 객체는 URL을 의미에 따라서 별도의 프로퍼티로 제공하고 있다. 

console.log(location.protocol, location.host, location.port, location.pathname, location.search, location.hash)

- URL 변경하기 

현재 문서를 http://egoing.net으로 이동한다. // 상황에 이동시켜야하는 경우에

location.href = 'http://egoing.net';

아래와 같은 방법도 같은 효과를 낸다. 

location = 'http://egoing.net';

아래는 현재 문서를 리로드하는 간편한 방법을 제공한다.

location.reload(); ,   location.href = location.href


#### >> Navigator 객체

- cross browsing
- console.dir(navigatior) : 브라우저의 특성에 대한 정보를 알고 싶을때 원하는 property를 찾으면 됌.
-appName
-웹브라우저의 이름이다. IE는 Microsoft Internet Explorer, 파이어폭스, 크롬등은 Nescape로 표시한다.

-appVersion
-브라우저의 버전을 의미한다. 필자의 현재 브라우저 정보는 아래와 같다.

-userAgent
-브라우저가 서버측으로 전송하는 USER-AGENT HTTP 헤더의 내용이다. appVersion과 비슷하다.

-platform
-브라우저가 동작하고 있는 운영체제에 대한 정보다.


#### >> 창 제어
-window.open 메소드는 새 창을 생성한다.
-현대의 브라우저는 대부분 탭을 지원하기 때문에 window.open은 새 창을 만든다. 

-첫번째 인자는 새 창에 로드할 문서의 URL이다. 인자를 생략하면 이름이 붙지 않은 새 창이 만들어진다.
     
     <input type="button" onclick="open1()" value="window.open('demo2.html');" />
        
        function open1(){
       window.open('alert.html'); }
-두번째 인자는 새 창의 이름이다. _self는 스크립트가 실행되는 창을 의미한다.
     
     <input type="button" onclick="open2()" value="window.open('demo2.html', '_self');" />
     
     function open2(){
    window.open('demo2.html', '_self');}
-_blank는 새 창을 의미한다.

         <input type="button" onclick="open3()" value="window.open('demo2.html', '_blank');" />
         
         function open3(){
          window.open('demo2.html', '_blank');}
-창에 이름을 붙일 수 있다. open을 재실행 했을 때 동일한 이름의 창이 있다면 그곳으로 문서가 로드된다.

           <input type="button" onclick="open4()" value="window.open('demo2.html', 'ot');" />
           function open4(){
           window.open('demo2.html', 'ot');}
-세번재 인자는 새 창의 모양과 관련된 속성이 온다.
     
           <input type="button" onclick="open5()" value="window.open('demo2.html', '_blank', 'width=200, height=200, resizable=yes');" />
           
               function open5(){
    window.open('demo2.html', '_blank', 'width=200, height=200, resizable=no');}

## **DOM** 

Document Object Model 

- 웹페이지를 자바스크립트로 제어하기 위한 객체모델
- window객체의 document 프로퍼티를 통해서 사용할 수 있다.  
- 문서 제어

#### >> 제어 대상찾기

#### document.getElementsByTagName
- TagName안의 Eleme`nts들을 얻는 것
- 인자로 전달된 태그명에 해당하는 객체들을 찾아서 그 리스트를 NodeList라는 유사 배열에 담아서 반환한다.

#### document.getElementsByClassName
- class 속성의 값 'active'를 기준으로 객체를 조회할수도 있다.

#### document.getElementById
- id값을 기준으로 객체를 조회한다. 성능면에서 가장 우수하고 많이사용한다.

#### document.querySelector 
- css 선택자의 문법을 이용해서 객체를 조회 

#### document.querySelectorAll
- document.querySelector 와 동일하지만 모든객체를 조회한다는 점에서 차이점이 있다.


#### >> jQuery (라이브러리의 일종?)
- jQuery는 DOM을 내부에 감추고 보다 쉽게 웹페이지를 조작할 수 있도록 돕는 도구
- ![image](https://user-images.githubusercontent.com/78002734/125951463-562e679c-5c85-4e6f-9e2d-e27ec06ba37d.png)
- ![image](https://user-images.githubusercontent.com/78002734/125951498-d701f2a7-f3b0-4dab-b3a5-6148f78de507.png)



