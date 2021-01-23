# [DOM(Document Object Model) 프로그래밍)]

모든 브라우저가 DOM 지원

DOM 객체

브라우저가 웹페이지(HTML)를 해석하고 랜더링 할 때, 인식된 각각의 태그들을 자바스크립트 객체로 생성하며 이 객체들을 DOM 객체라고 한다.

생성되는 DOM 객체들은 부모 자식 관계를 적용하여 트리구조로 구성한다.



<body>

<h1> .... </h1>

<ol>
    <li> ... </li>
    <li> ... </li>
</ol>

</body>

​		document

​		body

h1        ol

... li             li

​	....			...



DOM 프로그래밍에서 익혀야하는것

1. 동적인 처리를 하려는 태그의 DOM 객체를 찾는 방법

   document.getElementsByTagName("태그명")  ----> DOM객체배열에 담아서 리턴, 없으면 빈 배열객체 리턴

   document.getElementsById("id속성값")  ---->  DOM객체

   document.getElementsByClassName("class속성값")  ---->  DOM객체배열

   document.querySelectorAlll("CSS선택자")   --->  DOM객체배열 (몇개 찾아질지 모를 때)

   document.querySelector("CSS선택자")   --->  DOM객체  (분명히 한개일때)

값이 없다 = undefined

객체가 없다 = null



DOM 객체 타입 : Element 타입, Attribute 타입, Text 타입



2. 찾은 DOM 객체를 가지고 필요한 동적처리를 구현하는 방법

   - 컨텐트 변경하기

     **dom. innerHTML  =  "<p>새로운내용</p>"**  --- 태그와 함께 지정할 때

     **dom.textContent = "새로운 내용"**   --- 텍스트만 지정할때

   - 스타일 바꾸기

     dom.style.CSS속성명 = CSS 속성값

     예) dom.style.color = "red"

     ​		dom.style.background**-c**olor = "yellow"

     ​		dom.style.background**C**olor = "yellow"

   - 이벤트 핸들러 등록하기

     ​	구현방법 : 3가지

     1. 인라인 이벤트 모델 (지역적 방식) - 태그마다 속성으로 정의한다.

        <태그명 on 이벤트명="이벤트핸들러코드">

     2. 고전 이벤트 모델 (전역적 방식) - script 태그 안에 정의

        DOM 객체를 찾는다.

        dom.on이벤트명 = fuction() { ...... }

     3. 표준 이벤트 모델 (전역적 방식) - script 태그 안에 정의

        DOM 객체를 찾는다.

        dom.addEventListener("이벤트명", fuction() { ......  })

   

   http://localhost:8000/edu/jsexam/dom/exam1.html

   ```html
   <!DOCTYPE html>
   <html>
   <head>
   <meta charset="UTF-8">
   <title>Insert title here</title>
   </head>
   <body>
   <h1>컨텐트1</h1>
   <h1>컨텐트2</h1>
   <h1>컨텐트3</h1>
   <h1>컨텐트4</h1>
   <h2>컨텐트5</h2>
   <script src="../util.js"></script>
   <script>
   var h1dom = document.getElementsByTagName("h1");
   write(h1dom.length, "h3");
   for(var i=0; i <h1dom.length; i++)
      writeColor(h1dom[i].textContent, "h4", "red");
   var h2dom = document.getElementsByTagName("h2");
   writeColor(h2dom[0].textContent, "h2", "green");
   writeColor(h1dom[0], "h2", "blue");
   writeColor(h2dom[1], "h2", "blue");
   var h5dom = document.getElementsByTagName("h5");
   writeColor(h5dom.length, "h2", "magenta");
   </script>
   </body>
   </html>
   ```

![image-20210122131453252](C:\Users\jinsujeong\AppData\Roaming\Typora\typora-user-images\image-20210122131453252.png)

writeColor(h1dom[i].textContent, 을 읽어옴.

```
<script src="../util.js"></script>
<script src="/edu/jsexam/util.js"></script>
<script src="http://localgost:80000/edu/jsexam/util.js"></script>
```

상대 path / 절대 path/ 전체 URL



http://localhost:8000/edu/jsexam/dom/exam1_1.html

```html
<script>
function myf() {
    var h1dom = document.getElementsByTagName("h1");
    console.log(h1dom.length);
    for(var i=0; i <h1dom.length; i++)
       console.log(h1dom[i].textContent);
    var h2dom = document.getElementsByTagName("h2");
    console.log(h2dom[0].textContent);
    console.log(h1dom[0]);
    console.log(h2dom[0]);
    var h5dom = document.getElementsByTagName("h5");
    console.log(h5dom.length);
}
</script>
</head>
<body onload="myf()">
<h1>컨텐트1</h1>
<h1>컨텐트2</h1>
<h1>컨텐트3</h1>
<h1>컨텐트4</h1>
<h2>컨텐트5</h2>
</body>
</html>
```

페이지 로딩이 끝나면 myf() 함수를 호출해줘.

![image-20210122133645373](C:\Users\jinsujeong\AppData\Roaming\Typora\typora-user-images\image-20210122133645373.png)



http://localhost:8000/edu/jsexam/dom/exam2.html

![image-20210122133756769](C:\Users\jinsujeong\AppData\Roaming\Typora\typora-user-images\image-20210122133756769.png)

```html
</head>
<body>
<script src="../util.js"></script>

<h1 id="t1">컨텐트1</h1>
<h2 id="t2">컨텐트5</h2>
<p id="t3">컨텐트2</p>
<div id="t4">컨텐트2</div>
<img id="t5" src="../../images/totoro.png" width="100">
<hr>
<output id="p"></output>
<hr>
<script>
// 고전이벤트모델
window.onload = function() {
   var dom1 = document.getElementById("t1");
   console.log(dom1);
   console.log(dom1.textContent);
   var dom2 = document.getElementById("t3");
   console.log(dom2);
   var dom3 = document.getElementById("t4");
   console.log(dom3);
   var dom4 = document.getElementById("t5");
   console.log(dom4);
   console.log(dom4.getAttribute("src"));
   console.log(dom4.src); 
   var dom5 = document.getElementById("p");
   dom5.innerHTML = "<h2>"+new Date().toLocaleString()+"</h2>";
   //dom5.textContent = "<h2>"+new Date().toLocaleString()+"</h2>";
}
</script>
</body>
</html>
```

getAttribute("src") : 태그에 정의되어있는 속성명을 가져옴.

src 속성의 값을 가공하지 않고 그대로 추출. 할당되어있는 그대로

dom4.src : 실제 URL 문자열로 가공해서 보여줌. 

dom5.innerHTML = "<h2>"+new Date().toLocaleString()+"</h2>"; 

: 테스트한 시간 그대로 들어감. (태그와 함께 집어 넣을 때 사용)

```
dom5.textContent = "<h2>"+new Date().toLocaleString()+"</h2>";
```

: 태그도 문자열로 출력해줌.



http://localhost:8000/edu/jsexam/dom/exam3.html

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
<script src="../util.js"></script>
</head>
<body>
<h1 id="test">DOM객체를 찾자</h1>
<h1>ㅋㅋㅋㅋㅋㅋㅋ</h1>
<hr>
<script>
var dom = document.getElementsByTagName("h1");
write(dom, "h2");
write(dom[1], "h2");
write(dom[1].textContent, "h2"); // innerText
write(dom[1].innerHTML, "h2");
hr();
dom = document.getElementById("test");
write(dom, "h2");
write(dom.textContent, "h2");
window.setTimeout(function() {
   dom.innerHTML = "오늘은 불금";
   dom.style.color ="red";
   dom.style.backgroundColor ="lime";
}, 5000);
</script>
</body>
</html>
```

window.setTimeout 5초 후에 다음 함수를 수행하시오.

![image-20210122140454746](C:\Users\jinsujeong\AppData\Roaming\Typora\typora-user-images\image-20210122140454746.png)

http://localhost:8000/edu/jsexam/dom/exam4.html

![image-20210122140654033](C:\Users\jinsujeong\AppData\Roaming\Typora\typora-user-images\image-20210122140654033.png)

```html
</head>
<body>
<h1>시간정보 출력하기</h1>
<hr>
<button onclick="startTime()">시간을 알려주라옹...</button>
<button onclick="stopTime()">시간 출력을 종료하라옹...</button>
<output></output>
<script>
var target = document.getElementsByTagName("output")[0];
function startTime() {
   var d = new Date();
   target.innerHTML = "<h2>"+d.toLocaleString()+"</h2>";
}
function stopTime() {
   target.innerHTML = "";
}
</script>
</body>
</html>
```

클릭하는 시점에 따라 현재 시간 정보 출력함.

```html
target.innerHTML += "<h2>"+d.toLocaleString()+"</h2>";
```

= 대신에 += 입력하면 계속 append 처리가 되면서 출력됨.

![image-20210122141336096](C:\Users\jinsujeong\AppData\Roaming\Typora\typora-user-images\image-20210122141336096.png)

http://localhost:8000/edu/jsexam/dom/exam5.html

![image-20210122141459631](C:\Users\jinsujeong\AppData\Roaming\Typora\typora-user-images\image-20210122141459631.png)

```html
<body>
<h1 style="text-shadow: 2px 2px 3px gray">세 가지 이벤트 모델</h1>
<hr>
<h2 onclick="f1(this);">인라인 이벤트 모델</h2>
<hr>
<h2 id="t1">고전 이벤트 모델</h2>
<hr>
<h2 id="t2">표준 이벤트 모델</h2>
<hr>
<script>
   function f1(p) {
      alert(p.textContent);
      alert(document.querySelectorAll('h2')[0].textContent);
      //alert(this.textContent);
   }
   var dom2 = document.querySelector('#t1');
    var dom3 = document.querySelector('#t2');
   function f2(e) {
      alert(dom2.textContent);
      alert(this.textContent);
      alert(e.target.textContent);
   }
   function f3(e) {
      alert(dom3.textContent);
      alert(this.textContent);
      alert(e.target.textContent);
   }    
    dom2.onclick = f2;  //고전
    dom3.addEventListener("click", f3); // 표준
</script>
</body>
```

onclick="f1(this);">인라인 이벤트 모델 : 클릭하면 fi 을 호출하시오.

this : h2 태그에 대한 dom 객체. 이벤트 타겟 객체

alert(p.textContent);
alert(document.querySelectorAll('h2')[0].textContent);

추출되는 결과 같음.

그외의 this는 widow 객체



var dom2 = document.querySelector('#t1');   이 때, #은 id



마우스 올리기만해도 되는건 mouseover

http://localhost:8000/edu/jsexam/dom/exam6.html



```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
<h1>고전 이벤트 모델과 표준 이벤트 모델의 차이</h1>
<hr>
<button>고전 이벤트 모델</button>
<button>표준 이벤트 모델</button>
<script>
    var doms = document.querySelectorAll("button");
   var dom1 = doms[0];
   var dom2 = doms[1];
   
   dom1.onclick = function () {
                         alert("첫 번째 핸들러 수행(고전)");
                       };
   dom1.onclick = function () {               
                         alert("두 번째 핸들러 수행(고전)");
                       };
   dom2.addEventListener("click", 
                          function () { alert("첫 번째 핸들러 수행(표준)");});
   dom2.addEventListener("click", 
            function () { alert("두 번째 핸들러 수행(표준)");});
    dom2.addEventListener("click", 
            function () { alert(location.href);}); 

</script>
</body>
</html>
```

-  고전 이벤트 핸들러를 하나만 등록할 수 있음.

  나중 핸들러가 기존것을 대체해버림. 두번째 핸들러 수행만 가능

- 표준 이벤트 핸들러를 몇 개이든 등록가능 (등록 순으로 나옴) < 유지보수 좋음 >

- location.href : 현재 보고 있는 URL 정보 담는다.



http://localhost:8000/edu/jsexam/dom/exam7.html

```html
<body>

<form name="fm">
   <select id="choice" onchange="go();">
      <option value="">---관심있는 기술을 선택해 주세요---</option>
      <option value="http://www.w3schools.com/js/default.asp">Learn JavaScript</option>
      <option value="http://www.w3schools.com/js/js_htmldom.asp">Learn HTML DOM</option>
      <option value="http://www.w3schools.com/jquery/default.asp">Learn jQuery</option>
      <option value="http://www.w3schools.com/xml/ajax_intro.asp">Learn AJAX</option>
      <option value="http://www.w3schools.com/js/js_json_intro.asp">Learn JSON</option>
   </select>
</form>
<script>
//window.alert(location.href);
function go(){ 
   //location.href = document.getElementById("choice").value;
   location.href = document.querySelector("#choice").value;
   //location.href = "http://www.naver.com/";
}
</script>
</body>
```

페이지 이동

"#choice").value   id = choice 의 value 값에 맞게 페이지 이동

document.**getElementById("choice")**.value;  혹은

document.**querySelector("#choice")**.value;