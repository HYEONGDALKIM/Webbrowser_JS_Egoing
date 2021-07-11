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

최근에는 console.log 를 많이 써서 디버깅의 용도로는 잘 쓰지 않는다.

**confirm** -  확인을 누르면 true, 취소를 누르면 false를 리턴한다.
![image](https://user-images.githubusercontent.com/78002734/125197164-94d72980-e297-11eb-9300-aa2671f02531.png)

**prompt** - 사용자가 입력한 값을 받아서 JS가 얻어 낼 수 있는 기능 

![image](https://user-images.githubusercontent.com/78002734/125197155-8db01b80-e297-11eb-9a1b-ef40c3f8af21.png)
