http://localhost:8000/edu/jsexam/exam8_1.html

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
    <style>
        h1 {
            color : red;
            }
        h2 {
            color : blue;
        }
        h3 { color : magenta;
        }
        h4 {
            color: green;
            }
            button {
            padding : 10px;
            border-radius :5px;
            color:orange;
            font-weight : bold;
            }
    </style>
</head>
<body>
<!-- <h1>테스트</h1>--->
<script>
/*
    1부터 10사이의 난수를 추출하여(Math.random(),Math.floor())
    1~3 사이의 값이 추출되면 메시지를 <h2> 태그로 출력(document.write())
    4~6 사이의 값이 추출되면 메시지를 <h3> 태그로 출력
    7~9 사이의 값이 추출되면 메시지를 <h4> 태그로 출력
    10 이 추출되면 1부터 10까지의 합을 구해서 <h1> 태그로 출력
*/
    var num = Math.floor(Math.random()*10)+1
    document.write("<button>추출된 값 : " + num + "</button>");
    if (num < 4) {
        document.write("<h2>1~3사이의 숫자가 출력되었어요.</h2>");
        }
    else if (num < 7) {
        document.write("<h3>4~6사이의 숫자가 출력되었어요.</h3>");
        }
    else if (num < 10) {
        document.write("<h4>7~9사이의 숫자가 출력되었어요.</h4>");
        }
    else {
        var result = 0 ;
        for (var n=1; n <=10; n +=1)
            result += n
        document.write("<h1>1~10사이의 합 : "+result+"</h1>");
        }
</script>
</body>
</html>
```



> css 주석  : /* */
>
> 자바스크립트 주석 : // (단일행 주석), /* */ (다중행주석)
>
> html 주석 : <!--     -->



식을 적당히 만들어줘서 써야한다.

**Math.floor** : 소수점 이하를 날려버린다.  실수를 정수로.

**Math.floor(Math.random()*10)** 하면 0~9 출력

**Math.floor(Math.random()*10)+1** 해야 1~10 출력

![image-20210121101307646](C:\Users\jinsujeong\AppData\Roaming\Typora\typora-user-images\image-20210121101307646.png)



**for 반복문** : 초기식, 조건식, 증감식으로 구성되는 for 문 - **for(초기식;조건식;증감식)**

**forin 반복문** : 배열이나 객체를 가지고 반복을 처리하는 for문 - **for(인덱스(키)를 저장할 변수정의 in 배열 또는 객체)**



## [배열(파이썬의 리스트 객체와 거의 동일)]

- 여러 데이터들을 하나의 묶음으로 다루고자 할 때 사용

- 묶을 수 있는 데이터의 갯수에 제한이 없고, 데이터 타입도 제한이 없다.(섞어도 됨)

- 자바스크립트의 배열도 **객체**로 취급된다.

- 배열 생성 방법과 배열 사용 방법

  - 배열 생성 방법

    - 배열 리터럴 방법 - [1,2,3,4,5], ['aaa', 100, true, 3.4], [], [,,,,,]

    - API를 이용하는 방법 - new Array (1,2,3,4,5) , new Array ('aaa', 100, true, 3.4),

      ​                                      new Array(), new Array(8)

      

  - 배열 사용 방법

    배열의 크기(배열을 구성하는 element의 갯수) : 배열객체의 length 라는 속성(변수)의 값을 사용

    배열의 요소(원소, element)를 접근(l-value, r-value 모두 가능) : [0부터 시작하는 인덱스]

  

  http://localhost:8000/edu/jsexam/exam9.html

  

  ```html
  <!DOCTYPE html>
  <html>
  <head>
  <meta charset="UTF-8">
  <title>Insert title here</title>
  </head>
  <body>
  <h1>배열 생성과 활용(1)</h1>
  <hr>
  <script>
  var a1 = [ ];
  document.write("<h3>"+ typeof a1 +"</h3>");
  document.write("<h3>"+ Array.isArray(a1) +"</h3>");
  document.write("<h3>"+ a1.length +"</h3>");
  document.write("<h3>"+ a1[0] +"</h3>");
  document.write("<hr>");
  a1[4] = 100;
  document.write("<h3>"+ a1.length +"</h3>");
  for(var i=0; i < a1.length; i++)
     document.write("<h4>"+ a1[i] +"</h4>");
  document.write("<hr>");
  for(var i in a1)  // for(int data : ary)-java, for data in a1 :
     document.write("<h4>"+ a1[i] +"</h4>");
  document.write("<hr>");
  var a2 = [10, '가나다', true, 3.5];
  for(var i in a2)  // for(int data : ary)
     document.write("<h4>"+ typeof a2[i] + ":" + a2[i] +"</h4>");
  </script>
  </body>
  </html>
  ```

  ![image-20210121103608415](C:\Users\jinsujeong\AppData\Roaming\Typora\typora-user-images\image-20210121103608415.png)

a1에 비어있는 배열을 대입함.

**typeof **: 단항 연산자 이다. 배열 객체의 타입을 출력

object(객체)

**Array.isArray(a1)** : 리턴 값이 true 면 array, false면 array x

a1[0] : 첫 번째 원소를 꺼내 겠다. 없는 원소 꺼내라해서 undefined 출력

a1[4] = 100 : a1 의 다섯번째 원소에 100을 대입하겠다.

--> 방이 5개 만들어지면서, 다섯번째 원소에 100을 넣음. 나머지 방은 undefined

이 상태로 a1.length 추출하면 5나옴.

for문으로 다섯개의 원소를 각각 출력함. ( undefined도 확인 가능)

```html
for(var i in a1)  // for(int data : ary)-java, for data in a1 :
   document.write("<h4>"+ a1[i] +"</h4>");
```

forin문은 undefined 무시하고 undefined 아닌 애들만 반복처리한다.



http://localhost:8000/edu/jsexam/exam10.html

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
<h1>배열 생성과 활용(2)</h1>
<hr>
<script>
var a1 = new Array();  // [ ]
var a2 = new Array(10); // 크기 [,,,,,,,,,]
var a3 = new Array('가'); // 원소값 ['가']
var a4 = new Array(10, 20); // 원소값 [10, 20]
var a5 = new Array(1,2,3,4,5); // 원소값 [1,2,3,4,5]
/* window.alert(a1.length);
window.alert(a2.length);
window.alert(a3.length);
window.alert(a4.length);
window.alert(a5.length); */
document.write(a1 + "<br>");
document.write(a2.toString() + "<br>");
document.write(a3.toString() + "<br>");
document.write(a4.toString() + "<br>");
document.write(a5.toString() + "<br>");
var d = new Date();
document.write(d.toString() + "<br>");
document.write(d + "<br>");
document.write(d); //자동으로 d.toSting  결과 리턴
</script>
</body>
</html>
```

 window.alert(a1.length) = 0

window.alert(a2.length)=10

window.alert(a3.length)=1

window.alert(a4.length)=2
window.alert(a5.length)=5



document.write(a1.toString() ) 하면 원소가 없어서 아무것도 안나옴.

**toString()** : 배열객체에 대한 정보를 ,와 함께 하나의 문자열로 리턴해주는 역할. 생략 가능.

document.write(a2.toString() ) 하면 ,,,,,,,,, 나옴.

![image-20210121110902176](C:\Users\jinsujeong\AppData\Roaming\Typora\typora-user-images\image-20210121110902176.png)

http://localhost:8000/edu/jsexam/exercise1.html

파일명 : exercise1.html
1. 다음 값들을 저장하여 배열을 생성한다.
    10, 5, 7,21, 4, 8, 18

2. 모든 원소 값들을 더하여 다음 형식으로 HTML 첫 번째 제목 크기(<h1>)로
    출력한다.(document.write())
    모든 원소의 합 : XX

3. 최대값과 최소값을 구해서 순서없는 리스트 형식(<ul>)으로 출력한다.
     최대값 : XX
     최소값 : XX

  

> 배열값 중 최대 또는 최소값 찾는 방법
>
> 최대값을 구하기 위해서 Function.prototype.apply()를 사용할 수 있다.
>
> <<예시>>
>
> var myArray = [-3, -2, 1, 3, 5];
> var max = Math.max.apply(null, myArray);
>
> 5 // 최대값 5가 출력됨

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
<h1>배열 생성과 활용 실습</h1>
<hr>
<script>
var a1 = new Array(10,5,7,21,4,8,18);
var result = 0 ;
for(var i in a1)
    result += a1[i]
    document.write("<h1>모든 원소의 합 : "+result+"</h1>");
document.write("<ul>");
var max = Math.max.apply(null, a1);
document.write("<li>최대값 : "+max +"</li>");
var min = Math.min.apply(null, a1);
document.write("<li>최소값 : "+min +"</li>");
document.write("</ul>");
</script>
</body>
</html>
```



http://localhost:8000/edu/jsexam/exam11.html

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
<h1>배열 객체의 주요 메서드 활용</h1>
<hr>
<script>
var ary = ['둘리', '또치', '도우너', '희동이', '고길동']
document.write(ary + "<br>");
var ary2 = ary.sort();
document.write(ary + "<br>");
document.write(ary2 + "<br>");
document.write("<hr>");
var ary3 = [30, 11, 5, 27, 9]
document.write(ary3 + "<br>");
var ary4 = ary3.sort(function(a, b){ return a-b;});
document.write(ary3 + "<br>");
document.write(ary4 + "<br>");
document.write("<hr>");
var ary5 = [ ];
ary5.push(100);
ary5.push(200);
ary5.push(500);
document.write(ary5 + "<br>");
</script>
</body>
</html>
```

![image-20210121132351580](C:\Users\jinsujeong\AppData\Roaming\Typora\typora-user-images\image-20210121132351580.png)

숫자 < 대문자 < 소문자 < 한글

ary.sort() : 오름차순 정렬

ary도 ary1도 모두 정렬되서 나옴.

**ary4 = ary3.sort();**   배열의 원소값을 문자열로 간주하고 sorting 함.(디폴트)  --> 출력값 : [11,27,30,5,9] 맨앞글자 기준으로 sorting 해버림.

**ary3.sort(function(a, b){ return a-b;});**  : 숫자 기반의 오름차순

**ary3.sort(function(a, b){ return b-a;});**  : 숫자 기반의 내림차순



var ary5 = [ ]; 비어있는 배열 생성

ary5.push(100);  : 리스트의 append와 유사, 맨뒤에 추가해주는 역할

ary5.push(200);
ary5.push(500);

https://www.w3schools.com/jsref/jsref_sort.asp



### [함수 : 일급 객체를 만족한다.]

- 함수 만드는 방법

  - 선언적 함수정의(명시적 함수정의)

    function 함수명 ([매개변수...]) {

       			함수의 수행 코드들....

    ​				return 리턴값;

    }

  - 함수 표현식(함수 리터럴)

    var 변수 =  function  ([매개변수...]) {

       			함수의 수행 코드들....

    ​				return 리턴값;

    }

​	(1) 일급 객체로 취급된다. 함수를 변수에 담아서 사용(호출)할 수 있고,  함수 호출시 아규먼트로 전달 가능함.

​			리턴값으로 함수를 전달 가능

​	(2) 함수를 호출할 때 함수에 정의된 매개변수만큼 아규먼트를 전달하지 않아도 호출 가능하다.

​	(3) 함수가 값을 리턴하지 않으면 undefined 가 자동으로 리턴된다. (파이썬은 None)

​	(4) 가변인수를 지원한다. 함수 호출시 아규먼트의 갯수에 제한이 없는 함수를 만들 수 있다.

​			-----> 가변인수 함수를 정의할 때는 매개변수 정의를 생략하고 함수 호출시 자동으로 만들어지는 

​						arguments라는 배열을 활용한다.

​	(5) 기본값을 갖는 매개변수 정의를 할 수 있다.





- 함수 사용하는 방법 -> 호출, r-value

  ​	함수명([아규먼트...]);

  ​	var r = 함수명([아규먼트...]);

http://localhost:8000/edu/jsexam/exam12.html

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
<h1>함수 정의와 활용(1)-선언적 함수 정의</h1>
<hr>
<script>
f1();
document.write("<hr>")
function f1() {
   document.write('f1() 호출<br>');
}
function f2(p1, p2) {
   document.write('f2() 호출-'+(p1+p2)+'<br>'); 
}
f1();
f2(10,20);
document.write('<hr>');
var result1 = f1();
var result2 = f2(100,200);
document.write('result1 : '+result1+' result2 : '+result2);
if(result1 == undefined) {//if(!result1) {
   document.write('<br>리턴값이 없군요!!');
}
document.write('<hr>');
f1(100);
f2(100);
</script>
</body>
</html>
```

**선언적 함수 정의**

자바스크립트는 함수정의를 쭉 스캐닝함. 밑에 함수 정의가 되어있더라도 위에서 함수 호출 가능하다.

function f1()  : () 괄호 생략 불가



매개변수가 없더라도 전달해도 error 안남.

http://localhost:8000/edu/jsexam/exam13.html

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
<h1>함수 정의와 활용(2)-표현식 함수 정의</h1>
<hr>
<script>
//f1();
//document.write("<hr>")
var f1 = function () {
   document.write('f1() 호출<br>'); 
}
var f2 = function (p1, p2) {
   document.write('f2() 호출-'+(p1+p2)+'<br>'); 
}
f1();
f2(10,20);
document.write('<hr>');
var result1 = f1();
var result2 = f2(100,200);
document.write('result1 : '+result1+' result2 : '+result2);
if(result1 == undefined) {//if(!result1) {
   document.write('<br>리턴값이 없군요!!');
}
document.write('<hr>');
f1(100);
f2(100);
document.write(typeof f1 + '<br>');    
document.write(typeof f2 + '<br>');    
</script>
</body>
</html>
```

**표현식 함수 정의**

스캐닝하면서, 선언적함수정의가 있는지 확인함. 전역변수 선언을 인식함.

첫번째 행부터 error가 나서 출력이 안됨. (그래서 주석처리함.)

f1이 정의된 줄 알지만, 아직 아무값도 안갖고 있는 함수다.

반드시 만들고 나서 호출해야한다.

밑에서 호출할 때는 어떤 방법을 쓰든 상관이 없다.

![image-20210121143624021](C:\Users\jinsujeong\AppData\Roaming\Typora\typora-user-images\image-20210121143624021.png)

http://localhost:8000/edu/jsexam/exam14.html

버튼 태그에 클릭 이벤트가 발생했을 때 , 경고창 뜨게 하고 싶음.

이벤트 : 마우스 , 키보드, 등등 다양함.

이벤트핸들러를 구현할 때 함수로 구현한다.

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
<h2>함수에서 데이터의 타입채크</h2>
<hr>
<button onclick="clickProcess(100);">숫자</button>
<button onclick="clickProcess('100');">문자열</button>
<button onclick="clickProcess(true);">논리값</button>
<button onclick="clickProcess(function(){ });">함수</button>
<button onclick="clickProcess([ ]);">배열</button>
<button onclick="clickProcess({ });">객체</button>
<button onclick="clickProcess();">????</button>
<script>
function clickProcess(p) {
   if (typeof p == "number") {
      alert("숫자 전달!!");
   } else if (typeof p == "string") {
      alert("문자열 전달!!");
   } else if (typeof p == "boolean") {
      alert("논리값 전달!!");
   } else if (typeof p == "function") {
      alert("함수 전달!!");
   } else if (typeof p == "object") {
      if (Array.isArray(p))
         alert("배열객체 전달!!");
      else 
         alert("객체 전달!!");
   } else if (typeof p == "undefined") {  // p == undefined
      alert("전달된 아규먼트 없음!!");
   }  
}
</script>
</body>
</html>
```

clickProcess(p) : p라는 매개변수 

typeof p == "number"   : 인용부호 붙여서 반드시 문자열로 비교해야함.

아무것도 전달 되지 않았을 경우, typeof p == "undefined"  혹은 p == undefined 로 체크함.

(인용부호 붙이기)                       (인용부호 붙이지 않기)

![image-20210121143656127](C:\Users\jinsujeong\AppData\Roaming\Typora\typora-user-images\image-20210121143656127.png)

http://localhost:8000/edu/jsexam/exam15.html

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
<h1>가변아규먼트 처리 함수 만들기</h1>
<hr>
<script>
function out() {
   document.write("아규먼트 갯수 : "+arguments.length+"<br>");
   for(var i=0; i < arguments.length; i++) 
      console.log(arguments[i]);
   console.log('-----------------------');
}

out();
out(10); out(10,20); out('a', 'b', 'c'); out(1,2,3,4,5,6,7,8);
</script>
</body>
</html>
```

함수 호출 동시에, arguments를 만듦. 이 함수가 호출될때 전달된 아규먼트들을 배열로 만들어서 넣어준다.

![image-20210121150615652](C:\Users\jinsujeong\AppData\Roaming\Typora\typora-user-images\image-20210121150615652.png)

console.log(arguments[i]);  : 사용자를 위한 게 아니라 개발자를 위해 사용하는 언어이다.

수행 결과가 뭐가 나오는지 확인하고 싶지만 , 브라우저 화면에 내보내지 않을때!



console.log('-----------------------') : 함수 호출 끝났음을 알려주는 명령어





함수명(10)

함수명([10,20,30])

함수명(function() {

​							.......

​							........

​					});

function sum() { .... }

var avg = function(){......}

함수명(sum);   함수 호출

함수명(avg);

함수명(sum()); 함수 결과 호출



http://localhost:8000/edu/jsexam/exam16.html

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
<h1>함수의 아규먼트 처리</h1>
<hr>
<script>
function pr(p) {
   document.write(typeof p + " : " + p + "<br>"); 
}
pr(100);
pr("100");
pr(true);
pr(3.5);
pr(new Array(1,2,3));
pr(new Date());
//prNum(10);
//document.write("ㅋㅋㅋㅋㅋㅋ");
</script>
<hr>
<script>
function prNum(p) {
   if(typeof p == "number")
      document.write("숫자 전달 : " + p + "<br>");
   else if (p == undefined)
      document.write("아규먼트를 전달하시오 : " + p + "<br>");
   else
      document.write(typeof p + " : " + p + "<br>"); 
}
prNum(100);
prNum("100");
prNum(true);
prNum(3.5);
prNum(new Array(1,2,3));
prNum();
pr(100000);
</script>
<hr>
<script>
function prAll() {
   for(var i=0; i < arguments.length; i++)
      document.writeln(arguments[i]);
   document.write("<br>");
   return arguments.length;
}
var r1 = prAll(100);
var r2 = prAll(1,2,3,4,5);
var r3 = prAll('a', 'b', '가', true);
var r4 = prAll();
document.write(r1 + "<br>");
document.write(r2 + "<br>");
document.write(r3 + "<br>");
document.write(r4 + "<br>");
</script>
</body>
</html>
```

![image-20210121172534662](C:\Users\jinsujeong\AppData\Roaming\Typora\typora-user-images\image-20210121172534662.png)

같은 스트립 태그에서는 상관없지만,

다른 스트립태그에서는 불가능하다.

위의 스트립트 태그의 정의된 함수를 아래 스트립태그에서 호출(수행) 가능함. (반대로는 안됨.)



document.write(arguments[i]); 띄어쓰기 없이 쭈욱 출력

document.writeln(arguments[i]);  띄어쓰기와 함께 출력



http://localhost:8000/edu/jsexam/exam17.html

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
<h1>아규먼트로 함수 전달하기(고차함수)</h1>
<hr>
<script>
function output(p) {
   if(typeof p == 'function') {
      p("ㅋㅋㅋ");
   } else {
      document.write("<h2>ㅋㅋㅋ : "+p+"</h2>");       
   }  
}
output("둘리");
output(function(param) { console.log(param);})
function myAlert(param) {
//var myAlert = function(param) {  
   window.alert(param);
}
output(myAlert);
</script>
</body>
</html>
```

output("둘리"); 호출시에는 



화면에 나올 때는 경고창 출력을 최우선으로 함.



http://localhost:8000/edu/jsexam/exam18.html

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
<h2>고차함수 활용 예</h2>
<hr>
<p>5초후에 이 화면은 바뀝니다..</p> 
<script>
   var displayDate = function () {
      var d = new Date();
      document.write(d.toLocaleString()+"<br>");
   };
   var time = 5000;
   window.setInterval(displayDate, time);
</script>
</body>
</html>
```

![image-20210121174627816](C:\Users\jinsujeong\AppData\Roaming\Typora\typora-user-images\image-20210121174627816.png)

Date() : 현재시간으로 초기화 되는 객체를 만듦.

toLocaleString() : 우리나라 관습에 맞게 연월일시분초로 출력해줌

window.setInterval(displayDate, time);  첫번째 아규먼트는 함수(하고자하는 일)로, 두번째 아규먼트는 

![image-20210121175010213](C:\Users\jinsujeong\AppData\Roaming\Typora\typora-user-images\image-20210121175010213.png)