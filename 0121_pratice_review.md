# 1월21일_1 실습

파일명 : exercise1.html
1. 다음 값들을 저장하여 배열을 생성한다.
10, 5, 7,21, 4, 8, 18
2. 모든 원소 값들을 더하여 다음 형식으로 HTML 첫 번째 제목 크기(`<h1>`)로
출력한다.(document.write())
모든 원소의 합 : XX
3. 최대값과 최소값을 구해서 순서없는 리스트 형식(`<ul>`)으로 출력한다.
 최대값 : XX
 최소값 : XX

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>배열 실습</title>
</head>
<body>
    <script>
        var arr = new Array(10, 5, 7, 21, 4, 8, 18);
        var sum = 0;
        var max = 10; // 초기값을 앞 숫자로 잡음.
        var min = 5;
        for(var i in arr)
        {
            sum += arr[i];
            if(max<arr[i])
                max = arr[i];
            if(min>arr[i])
                min = arr[i];
        }
        document.write("<h1>모든 원소의 합: "+sum+"</h1>");
        document.write("<ul>");
        document.write("<li>최대값: "+max+ "</li>");
        document.write("<li>최소값: "+min+ "</li>");
        document.write("</ul>");

    </script>
</body>
</html>
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>배열 실습</title>
</head>
<body>
    <script>
        var arr = new Array(10, 5, 7, 21, 4, 8, 18);
        var sum = arr[0];
        var max = arr[0];
        var min = arr[0];
        for(var i=1; i < arr.length; i += 1)
        {
            sum += arr[i];
            if(max<arr[i])
                max = arr[i];
            if(min>arr[i])
                min = arr[i];
        }
        document.write("<h1>모든 원소의 합: "+sum+"</h1>");
        document.write("<ul>");
        document.write("<li>최대값: "+max+ "</li>");
        document.write("<li>최소값: "+min+ "</li>");
        document.write("</ul>");

    </script>
</body>
</html>
```

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



파일명 : exercise2.html
1. 다음 기능을 처리하는 함수 sum()를 구현해 본다.
- 매개변수를 한 개 선언한다.
- 아규먼트가 아무값도 전달되지 않으면 리턴값 없이 리턴한다.
- 1부터 아규먼트로 전달된 숫자값 까지 합을 구하여 리턴한다.
2. 0부터 5사이의 난수를 하나 추출하여 아규먼트로 전달하면서 sum() 함수를 호출하는데
0이 추출된 경우에는 아규먼트 없이 호출한다.
호출한 다음
리턴값이 있으면 다음 형식으로 브라우저의 도큐먼트 영역 `<h2>` 태그와 함께 출력하고
호출 결과값 : XX
리턴값이 없으면 다음과 같이 브라우저의 도큐먼트 영역에 `<h3>` 태그와 함께 출력한다.
결과값이 없어요!!

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<script>
function sum(p) {
    if(p == undefined)
        return;
    else {
        var sump = 0;
        for(var n=1; n<=p; n++)
            sump += n;
        return sump;
   }
}

var num = Math.floor(Math.random()*6)
console.log(num)
var result;
if(num == 0)
    result = sum();
else
    result = sum(num);
if(result == undefined)
   document.write('<h3>결과값이 없어요!!</h3>');
else
   document.write('<h2>호출 결과값 :'+result+'</h2>');
</script>
</body>
</html>
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>sum 함수 구현</title>
</head>
<body>
    <script>
        function sum(num)
        {
            var sum = 0;
            if(num==undefined)
                return num;

            for(var i=1; i<=num; i++)
                sum += i;

            return sum;
        }

        var rand = Math.floor(Math.random()*6);
        var result;
        if(rand==0)
            result = sum();
        else
            result = sum(rand);

        if(result!=undefined)
            document.write("<h2>호출 결과값: " + result + "</h2>");
        else
            document.write("<h3>결과값이 없어요!</h3>");
    </script>
</body>
</html>
```

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<script>
    function sum(p) {
        if (typeof p == 'undefined')
            return;
        else {
            psum=0;
            for (var i=1; i<=p; i++)
                psum+=i;
            return psum;
        }
    }
    var num = Math.floor(Math.random()*6);
    var result;
    if (num == 0)
        result = sum();
    else
        result = sum(num);
    if(result == undefined)
        document.write('<h3>결과값이 없어요!!!</h3>');
    else
        document.write('<h2>호출 결과값 : ' + psum + '</h2>');
</script>
</body>
</html>
```