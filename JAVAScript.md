# 자바스크립트(JAVAScript)

- 웹 페이지의 동적인 처리를 구현하는 프로그래밍 언어이다.

- HTML 파일 안에 구현하는 프로그래밍 언어로서 인터프린터 언어이다.

- <script> 태그의 컨텐트로 작성하거나 HTML 태그에 정의된 속성의 값으로 작성한다.

- 구문

   - 파이썬 그리고 R과 많은 부분 비슷한 구문을 가지고 있습니다.

   - 세 개 언어 모두 인터프리터 언어로 분류된다.

     1. 변수 정의 방법과 처리 가능한 데이터 타입

     2. 연산자와 제어문

     3. 배열(array) - 파이썬 리스트

     4. 함수 정의 방법, 함수 사용 방법(호출)

     5. 함수는 일급 객체이다. 

     6. 객체 생성 방법 

        - 클래스를 가지고 객체를 생성하는 방법

        						 - { .... } 를 사용해서 객체를 생성하는 방법 - 객체리터럴

     7. 이벤트 처리하는 방법, DOM 객체를 통해서 HTML 태그를 제어하는 방법

     8. jQuery : JavaScript의 대표적인 API  - 간단한 자바스크립트 구현을 지원



css 는 스타일적인 것을 보조하고, 자바스크립트는 웹 페이지 구성하거나 action에 대한 처리 코드를 구성한다.



http://localhost:8000/edu/jsexam/exam1.html

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>자바스크립트 맛보기</title>
</head>
<body>
<h1>자바스크립트 코드 실행</h1>
<hr>
<button>클릭하세요</button>
<button><img src = "../images/kakao/g7.png" width="100"></button>
<script>
    var doms = document.getElementsByTagName("button");
    console.log(doms[0])
    console.log(doms[1])
    doms[0].onclick = function() {
        window.alert("텍스트 버튼이 클릭되었어요!!")
                                };
    doms[1].onclick = function() {
        window.alert("이미지 버튼이 클릭되었어요!!")
                                };
</script>
</body>
</html>
```

```html
var doms = document.getElementsByTagName("button");
```

이름이 button인 elment를 겟하면..

첫번째 버튼을 클릭했을때,  함수 실행



[] : 

{} : 

() : 

<> : 대소 관계 연산자



http://localhost:8000/edu/jsexam/exam1_1.html

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<h1>자바스크립트 맛보기-2</h1>
<hr>
<button onmouseover="window.alert('클릭하셨군요!!')">클릭해보세요</button>
<hr>
<button onclick="displayDate('red')">빨강</button>
<button onclick="displayDate('blue')">파랑</button>
<button onclick="displayDate('yellow')">노랑</button>
<hr>
<output id="target"></output>
<script>
    function displayDate(colorname) {
        var now = new Date();
        var strnow = now.getFullYear()+"년 " + (now.getMonth()+1)+"월 " + now.getDate()+"일";
        var targetDom = document.getElementById("target");
        console.log(targetDom);
        targetDom.textContent = strnow;
        targetDom.style.color = colorname;
    }
</script>
</body>
</html>
```



Date()  객체 생성해서 

getmonth()는 0부터 나옴..

괄호 (now.getMonth()+1) 꼭 붙여주어야함. (우선순위 숫자로! 안그럼 문자로 결합됨.)

document.getElementById("target"); 

id는 unique 하기 때문에 getElement 단수형으로 하나만 리턴해줌. 없으면 none리턴

target이라는 id 속성을 가진 객체를 찾아와라.

찾아온 oup 태그에 .textContent 는 strnow내용을 입력하고

찾아온 oup 태그에 .style.color 는 colorname 내용을 보여준다.



http://localhost:8000/edu/jsexam/exam2.html

```html
<body>
<h1>JavaScript의 변수 선언과 활용</h1>
<hr>
<script>
   var v1;
   document.writeln(v1+"<br>");
   v1 = 100;
   document.writeln(v1+"<br>");
   v1 = '가나다';
   document.writeln(v1+"<br>");   
   var v1 = true;
   document.writeln(v1+"<br>");   
   v1 = 123;
   document.writeln(v1+45+"<br>");    
   v1 = '123';
   document.writeln(v1+45+"<br>");    
</script>
<h1>JavaScript의 변수 선언과 활용</h1>
</body>
</html>
```

변수 만드는 법

var 키워드를 붙이고 변수 이름을 쓴다.

파이썬의 단일 행 주석 : #

자바스크립트의  단일행 주석 : //

자바스크립트 : 변수를 만들기는 했지만, 값을 안넣었을 경우 자동으로 undefined 가 들어간다.



파이썬 : True, False

자바스크립트 : true, false

R : TRUE, FALSE



숫자에 인용부호 붙이면 문자열로 인식됨. 

문자열 + 문자열 아닌 것 = 문자열로 바뀜



http://localhost:8000/edu/jsexam/exam3.html



```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
<h1>자바스크립트의 데이터 타입 채크</h1>
<hr>
<script>
   document.write("<h2>"+ typeof 100 +"</h2>");
   document.write("<h2>"+ typeof 3.14 +"</h2>");
   document.write("<h2>"+ typeof '가' +"</h2>");
   document.write("<h2>"+ typeof "abc" +"</h2>");
   document.write("<h2>"+ typeof '100' +"</h2>");
   document.write("<h2>"+ typeof true +"</h2>");
   document.write("<h2>"+ typeof undefined +"</h2>");
</script>
</body>
</html>
```





http://localhost:8000/edu/jsexam/exam4.html

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
<h1>자바스크립트의 변수 선언과 활용(2)</h1>
<hr>
<script>
   document.write("<ul>");
   var v1;
   document.write("<li>"+ v1 +"</li>");
   document.write("<li>"+ typeof v1 +"</li>");
   document.write("<li>"+ (v1+10) +"</li>");
   v1 = 100;
   document.write("<li>"+ v1 +"</li>");
   document.write("<li>"+ typeof v1 +"</li>");
   document.write("<li>"+ (v1+10) +"</li>");
   v1 = true;
   document.write("<li>"+ v1 +"</li>");
   document.write("<li>"+ typeof v1 +"</li>");
   document.write("<li>"+ (v1+10) +"</li>");
   v1 = "가나다";
   document.write("<li>"+ v1 +"</li>");   
   document.write("<li>"+ typeof v1 +"</li>");
   document.write("<li>"+ (v1+10) +"</li>");
   document.write("<ul>");
</script>
</body>
</html>
```

# 자바스크립트의 변수 선언과 활용(2)

------

- undefined
- undefined
- NaN
- 100
- number
- 110
- true
- boolean
- 11
- 가나다
- string
- 가나다10



NaN : Not a number 



http://localhost:8000/edu/jsexam/exam5.html



```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
<h1>자바스크립트의 연산자(1)</h1>
<hr>
<pre>
<script>
   document.writeln(10>5);
   document.writeln("abc">"ABC");
   var str = "가나다";
   document.writeln(str == "가나다");
   document.writeln(true == 1);
   document.writeln("100" == 100);
   document.writeln(true === 1);
   document.writeln("100" === 100);   
   document.writeln(10/3);
   document.writeln(10%3);
   var num=10;
   document.writeln(num++); // 출력은 10    --> 11 이 된 상태에서 다음 행으로 이동
   document.writeln(--num);  // 10   --> 11에서 10으로 만든 상태에서 10 출력
</script>
</pre>
</body>
</html>
```

# 자바스크립트의 연산자(1)

------

```
true
true
true
true
true
false
false
3.3333333333333335
1
10
10
```

pre 태그로 감싸서 출력하면 폰트 사이즈는 작아지고, 개행처리되어서 출력된다.

(html은 개행처리 자동으로 안되고, 띄어쓰기로 출력된다. 개행원하면 br 태그 붙였었음)



writeln 는 전달하라는 의미



true는 불변형

"100"은 string 형

=== 지원은 자바스크립트 밖에 없음

== : 타입 다른 것은 문제 되지 않는다.

=== : 동치 연산자 (데이터의 타입 같은지, 같도 동일한지)

10/3 : 나눗셈은 /

% : 나머지 구할 때

num++ : 현재 number 를 전달하고 나서 1을 증가시킴. (나중 증가)

--num : 먼저 감소 시키고 출력해라.

증감 연산자(주어진 피연산자의 값을 1증가(감소))

++변수 : 변수의 값을 1증가시키고 다른 연산을 수행

 변수 ++ : 다른 연산을 먼저 하고 나중에 변수의 값을 1 증가

++ 증가 연산자

-- 감소 연산자



http://localhost:8000/edu/jsexam/exam6.html

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
<h1>자바스크립트의 연산자(2)</h1>
<hr>
<pre>
<script>
   var num=window.prompt("숫자 하나를 입력해 주세요");
   // num이 짝수이면 "xx는 짝수"
   // num이 홀수이면 "xx는 홀수"
   num % 2 == 0 && document.writeln(num+"는 짝수");
   num % 2 == 0 || document.writeln(num+"는 홀수");
</script>
</pre>
</body>
</html>
```

입력받는 창이 뜨고,  입력후 enter 혹은 확인 버튼 누름

아무것도 입력하지 않고, 취소 버튼 누르면 null 값 출력

아무것도 입력하지 않고 확인버튼 누르면 null 문자열("") 출력



window.prompt("숫자 하나를 입력해 주세요") 는 무조건 **문자열** 타입으로나옴.



&& 논리 연산자  ---> and  :  앞의 식을 수행하고 참이면 두번째 실행(앞이 거짓이면 뒤가 실행x)

|| ---> or  : 앞의참이면 뒤 실행 x, 앞이 거짓이면 뒤 실행 O



1) num % 2 == 0 && document.writeln(num+"는 짝수");

2) if (num % 2 == 0)

 		document.writeln(num+"는 짝수");

둘다 같음. 



+연산을 제외하고, 사칙연산할 때, 자동으로 숫자로 바꿔서 연산을 해준다.

(+는 문자열로 결합해버리는 게 더 강함.)

다중행 주석  /*   */



```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
<style>
   span { color : red; }
</style>
</head>
<body>
<h1>자바스크립트의 연산자(2)</h1>
<hr>
<pre>
<script>
   var num=window.prompt("채크하려는 숫자를 입력해 주세요.");
   //window.alert(num+":"+isNaN(num));
   num = num.trim()
   if(isNaN(num) || num == '' || num == null ) 
      document.writeln("<span>숫자</span>를 입력해 주세요!!!");
   else {
      num % 2 == 0 && document.writeln(num+"는 짝수");
      num % 2 == 0 || document.writeln(num+"는 홀수");
   }
</script>
</pre>
</body>
</html>
```

window.prompt("채크하려는 숫자를 입력해 주세요.") 문자열로 담아서 리턴함.

isNaN : not a number 인가?(순수하게 숫자로 구성된 문자열인가?) 숫자면 FALSE, 아니면 TRUE

띄어쓰기(blank)하고 숫자 입력하더라도 FALSE 출력

num.trim() : 띄어쓰기(blank) 없애주는 역할

window.prompt 창이 뜨게 함.



실행구문이 여러개일 때는 {}로 묶어주어야한다.



http://localhost:8000/edu/jsexam/exam7_1.html



```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
<style>
   span { color : red; }
</style>
</head>
<body>
<h1>자바스크립트의 연산자(2)</h1>
<hr>
<pre>
<!--  세번 반복  -->
<script>     
   for(var su=1; su < 4 ; su++ ) {
      var num=window.prompt("채크하려는 숫자를 입력해 주세요.");
      //window.alert(num+":"+isNaN(num));    
      if(isNaN(num) || num == '' || num == null ) {
         document.writeln("<span>숫자</span>를 입력해 주세요!!!");
      } else {
         num % 2 == 0 && document.writeln(num+"는 짝수");
         num % 2 == 0 || document.writeln(num+"는 홀수");
      }
   }
</script>
</pre>
</body>
</html>
```

su++ 혹은 su =+1 혹은 su = su+1   : su 변수를 1 증가시켜라.

3번 반복 (횟수를 지정한 반복을 하고 싶을 때)



```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
<style>
   span { color : red; }
</style>
</head>
<body>
<h1>자바스크립트의 연산자(2)</h1>
<hr>
<pre>
<!--  사용자가 원할 때까지 반복  -->
<script>     
   while(true) {
      var num=window.prompt("채크하려는 숫자를 입력해 주세요.");
      //window.alert(num+":"+isNaN(num));    
      if(isNaN(num) || num == '' || num == null ) {
         document.writeln("<span>숫자</span>를 입력해 주세요!!!");
      } else {
         num % 2 == 0 && document.writeln(num+"는 짝수");
         num % 2 == 0 || document.writeln(num+"는 홀수");
      }
      var result = window.confirm("계속 수행할까요?");
      if(!result)
         break;
   }
</script>
</pre>
</body>
</html>
```

원할 때까지 반복!

var result = window.confirm("계속 수행할까요?");  물어본후

 if(!result)   // 파이썬의 not 연산자와 동일함.

리턴 값이 false(취소버튼누름)면 중단.



window.alert(): 사용자에게 메시지를 보여주고 확인 받는용도

window.prompt() : 사용자로부터 데이터를 입력받는 용도

window.confirm() : yes 또는 no 둘중 하나를 입력 받는 용도





API : Application Programming Interface

​		프로그래밍할 때 자주 구현되는 기능들을 미리 구현해 놓은 프로그램 

​		프로그래밍 언어마다 자기만의 API를 가지고 있으며, 개발 환경을 구축할 때

​		함께 설치되는 API를 표준 API라고 하며 개발자가 필요에 의해 추가로 설치하는 API들을 확장 API 또는 

​		third - party API 라고 한다.

​		C 언어 : 객체 지향 언어 아님. 함수 기반 언어. API도 함수로 만들어짐

​		JAVA : 객체 지향 언어. 클래스 (메서드)

​		python, JavaScript, R : 함수, 클래스(메서드)



## JavaScript의 제어문

- 조건 제어문 : if, (switch)
- 반복제어문 : for , while, (do ~ while)
- 분기제어문 : break, continue

if  (조건식)

​	수행문장;

if (조건식) {

​	수행문장;

​	수행문장;

}

if (조건식)

​	수행문장;

else

​	수행문장;



if (조건식)

​	수행문장;

else if (조건식)

​	수행문장;

else if (조건식)

​	수행문장;

else

​	수행문장;



### for 문

**일반(전통) for** :  for(초기화식;조건식;증감식){

​								반복수행문장}

​							for(변수정의와 초기화식; 반복처리를 계속할지 결정하는 조건식; 변수의 값을 변화시키는식)

​							for(var num = 1 ; num < 11; num +=1)   ---> 10번 반복

​							for(var num = 10; num >0; num -=1)  ---> 10번 반복        개발자 마음

​							for(var num = 10; num <20 ; num +=1)  ---> 10번 반복	

​							for(var num = 1; num<=50; num+=1 )   ---> 1부터 50까지의 값을 1씩 증가시키면서 처리하시오.

​							for(var num = 1; num<=50; num+=2 )   ---> 1부터 50까지의 값을 2씩 증가시키면서 처리하시오.

​	

**향상된 for, for-each , for-in** : for(변수 정의 in 배열(리스트) 또는 객체)

​												반복수행문장

​										a = [10,20,30,40,50]   // 자바스크립트에서는 배열, array이라고 칭함.

**파이썬** 							for data in a :   # 리터럴한 객체만 가능

​											print(data)  # 10  20 30 40 50 이 행 단위로 출력됨.

​										for (var i in a) {  // 다섯 번 수행하는데 index를 줌.

**자바스크립트**                     window.alert(i) ;  // ---> 0,1,2,3,4 출력

​											}

​								        for (var i in a)

​											window.alert(a[i]);



### while

while(조건식)

​	반복문장;



while (true)

​	무한반복문장;



break : 반복문을 종료해라.

continue : 다음 반복으로 계속해서 진행해라.



http://localhost:8000/edu/jsexam/exam8.html

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
<h1>자바스크립트의 랜덤값 처리</h1>
<hr>
<script>
for(var i=0; i <10; i++){
   var rand = Math.random();// 0.0<= rand < 1.0
   console.log(rand);
   console.log(rand*3);
   console.log(Math.floor(rand*3));
   console.log("-----------------------");    
   document.write(Math.floor(rand*3) +"<br>");
}
</script>
</body>
</html>
```

0 또는 1 또는 2

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
<h1>자바스크립트의 랜덤값 처리</h1>
<hr>
<script>
for(var i=0; i <10; i++){
   var rand = Math.random();// 0.0<= rand < 1.0
   console.log(rand);
   console.log(rand*6);
   console.log(Math.floor(rand*6));
   console.log("-----------------------");    
   document.write(Math.floor(rand*6) +"<br>");
}
</script>
</body>
</html>
```

0~5