스트립트 태그 여러개 작성 가능

http://localhost:8000/edu/jsexam/exam19.html

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
<h2>자바스크립트 변수의 종류</h2>
<hr>
<script src="util.js"></script>
<script>
var num1 = 100;
let num2 = 200;
const num3 = 300;
writeColor("num1 : " + num1, "h1", "red");
writeColor("num2 : " + num2, "h1", "green");
writeColor("num3 : " + num3, "h1", "blue");
hr()
num1 = '가';
num2 = '나';
//num3 = '다';
writeColor("num1 : " + num1, "h2", "red");
writeColor("num2 : " + num2, "h2", "green");
writeColor("num3 : " + num3, "h2", "blue");
hr()
var num1 = 3.5;
//let num2 = 4.7;
//const num3 = 5.3;
writeColor("num1 : " + num1, "h3", "red");
writeColor("num2 : " + num2, "h3", "green");
writeColor("num3 : " + num3, "h3", "blue");
</script>
</body>
</html>
```

- 스트립트 태그를 사용하고 컨텐트를 자바스크립트 코드 로 쓰기

- 독립된 파일로 만들어서 .js를 끌어오는 방법 (여러 html 파일에서 공통적으로 사용할 때 유용)

```html
<script src="util.js"></script>
```

**<<util.js>>**

```javascript
function write(content, tag) {
   document.write("<"+tag+">"+content+"</"+tag+">");  
}
function hr() {
   document.write("<hr>");
}
function writeColor(content, tag, color) {
   document.write("<"+tag+" style='color:"+color+"'>"+
           content+"</"+tag+">");   
}
function writeNewLine(content) {
   document.write(content+"<br>");    
}
```

구분할 수 있는 분리선 생성하는 hr 함수를 생성

아규먼트 하나 더 늘림. 내용, 태그 이름, 원하는 칼라이름

자동으로 br 태그가 붙게끔 만들어주는 writeNewLine(content) 생성

자바스크립트 소스파일로 독립된 파일로 끌어오게 함. (반드시 위에서 실행해야함.)

![image-20210122092053591](C:\Users\jinsujeong\AppData\Roaming\Typora\typora-user-images\image-20210122092053591.png)

같은 스크립트 내에서는 함수정의를 뒤에서 해도 상관없지만

다른 스크립트일 때는 위의 스크립트 태그의 함수 정의를 밑의 스크립트 태그에서 함수 적용만 가능하다.



변수 정의 :  

var v1 = 10    //--->  전역변수 생성 (함수 밖)

v1 = 100

var v1 = 1000   //---> 똑같은 이름 의 변수를 또 만들어도 error 안남 (대체해버림)

function f1() {

​	**var** v2 = 20   //----> 지역변수 생성 (함수 안)

​	var v2 = 200     //---> 똑같은 이름 또만들면 대체.

}



```html
<script src="과장님.js"></script>
```

```html
<script src="대리님.js"></script>
```

똑같은 이름의 전연변수 선언하면 대리님의 전역변수로 대체해버림

과장님 전역변수 못씀



ECMA



var, let, const

**var**는 값 바꾸는 것 허용. 같은 html 안에서 똑같은 이름의 변수 선언도 가능.

변수 선언할 때, **let**을 주고 밑에서 let 똑같은 이름 선언하면 error 뜸 (대체 방지)

값을 바꾸는 것까지는 허용.  똑같은 이름의 변수 선언은 불가하다. (좀더 안전)

**const**를 붙여놓으면, 상수로 사용되는 변수라서 한번 할당하면 못 바꿈(고정)-- error 남.

값을 못바꾸고 r-value로만 사용 가능

ex) const pi = 3.14



http://localhost:8000/edu/jsexam/exam20.html

```html
<script src="util.js"></script> 
<script>
var g_v = 100;
function scopeTest() {
   var l_v = 1000;
   writeNewLine("scopeTest() l_v : " + l_v);
   writeNewLine("scopeTest() g_v : " + g_v );
}
scopeTest();
try {
   writeNewLine("l_v : " + l_v  );
} catch(e) {
   writeNewLine(e);
}
writeNewLine("g_v : " + g_v );
</script>
```

l_v : 지역변수 값 출력

g_v : 전역 변수 값 출력

try 구문 

writeNewLine("l_v : " + l_v  ); 을 수행하다가 에러가 나면

writeNewLine(e); 수행해라.

에러 메세지 보내고 

writeNewLine("g_v : " + g_v ); 마저 수행해라







## [ 자바스크립트의 객체 생성 방법]

(1) 객체 리터럴 방법

(2) 클래스 (생성자 함수)를 이용하는 방법

​	new Array(), new Date()

(3) 내장 객체 : 개발자가 객체를 생성하지 않아도 자바 스크립트 엔진이 자동으로 생성해주는 객체

​	window, document, navigator, screen, DOM 객체들...



- 객체 리터럴 방법

  배열 객체 : [1, 'abc', true, 3.4]

  객체 : {속성명 : 속성값, 속성명 : 속성값, ... }

  ​			속성명 : 자바스크립트의 식별자 규칙(명명규칙), 문자로 시작, 문자, 숫자, _ 를 사용할 수 있다.

  ​			속성값 : 숫자, 문자열, 논리값, 배열, 객체, 함수(메서드)

  obj = {속성명1 : 100, 속성명2 : "둘리", 속성명3 : function()  {....}}

  obj. 속성명1 = 200

  obj. 속성명2  + "승리"

  obj.속성명3() 

  

  obj['속성명1'] = 200

  obj['속성명2'] + "승리"

  http://localhost:8000/edu/jsexam/exam21.html

```html
<body>
<h1>자바스크립트의 객체 생성과 사용(객체리터럴)</h1>
<hr>
<script src="util.js"></script>
<script>
   var obj = {
         name : "듀크",
         eat : function(food) {
            writeColor(this.name +"가 "+food+
                      "를 먹어요!!", "h3", "green");
         }
   }
   obj.eat("바나나");
   obj.eat("딸기");
   hr();
   writeColor(typeof obj, 'h2', "red");
   obj.project = "자바스크립트";
   obj.study = function() {
      writeColor(this.name +"가 "+this.project+
                "를 공부해요!!", "h3", "magenta");
   }
    obj.study();
    hr();
    for(var key in obj)
       write(key + " : " + obj[key], "h4");
    hr()
    write(obj.project, "h2");
    write(obj["project"], "h2");
    delete obj.study;
    for(var key in obj)
       write(key + " : " + obj[key], "h4");
</script>
</body>
```

![image-20210122102751986](C:\Users\jinsujeong\AppData\Roaming\Typora\typora-user-images\image-20210122102751986.png)

this. :  현재 객체