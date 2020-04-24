# What is Node.js?
- Node.js 는 다양한 플랫폼에서 구동할 수 있고, Javascript를 사용한 오픈소스 서버 언어입니다.

# Why Node.js?
> Node.js는 비동기적 프로그래밍에 사용됩니다.
일반적으로 웹 서버를 열고 클라이언트가 요청한 파일을 건내주는 역할을 합니다.

PHP or ASP가 파일을 다루는 방법:
1. 컴퓨터 파일 시스템에게 요청합니다.
2. 파일 시스템이 필요한 파일을 열고 읽는동안 기다립니다.
3. 클라이언트에게 컨텐츠를 반환합니다.
4. 다음 요청을 기다립니다.

Node.js가 파일을 다루는 방법:
1. 컴퓨터 파일 시스템에게 요청합니다.
2. 다음 요청을 기다립니다.
3. 파일시스템이 파일을 열고 읽을 때 컨텐츠를 반환합니다.

Node.js는 대기하는 시간을 없애고, 간단하게 다음의 요청을 처리합니다. 또한 하나의 thred, 비동기적, 막힘이 없는 프로그래밍언어로 메모리 효율적입니다.

## what Can Node.js Do?
- 동적 페이지 컨텐츠를 생성할 수 있습니다.
- 서버 파일을 열고 닫고 읽고 쓰고 지울 수 있습니다.
- form 데이터를 수집할 수 있습니다.
- Database와 연동 가능합니다.
  
## What is a Node.js File?
- Node.js files contain tasks that will be executed on certain events
- A typical event is someone tyring to access a port on server
- Node.js files must be initiated on the server before having any effect
- Node.js files have extension ".js"

# Getting Started
Node.js를 설치한 이후에 웹 브라우저에 "Hello World"를 출력해 봅시다.<br/>"myfist.js"이름을 가진 Node.js 파일을 만들고 아래와 같은 코드를 따라 작성해 봅시다.

```js
// myfirst.js
var http = require('http');

http.createServer(function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/html'});
  res.end('Hello World!');
}).listen(8080);
```
작성한 코드를 저장합니다. 이 코드는 누군가가 8080포트로 서버(현재 코드를 작성한 컴퓨터)에 접속하면 "Hello World"를 반환하라는 코드입니다. 아직 이 코드가 이해되지 않았다고해서 조급해 할 필요가 없습니다. 이 이후에 다시 설명할 겁니다.

## Command Line Interface
Node.js파일은 반드시 'Command Line Interface'를 통해 시작해야합니다.<br/><br/>CMI를 열기 위한 방법은 컴퓨터 OS에 따라 달집니다. 만약 Windows를 사용하고 있다면, [windowKey + E] 를 눌러 '실행' 창을 띄운다음 'Command Prompt'를 입력하거나 간단한게 'cmd'를 입력하여 실행할 수 있습니다.<br/><br/>위에서 작성한 파일 'myfirst.js' 파일의 위치로 이동하게 되면 아래의 이미지와 같은 상태가 됩니다.
![console_locate](./img/image1.png)
> windows에서 파일을 이동할 때에는 'cd' 커맨드를 사용해서 이동할 수 있습니다. 또한 파일 경로는 'myfirst.js'를 저장한 위치에 따라 다를 수 있습니다.

## Initiate the Node.js File
위에서 만든 파일은 만드시 node.js에 의해 시작되어야 합니다. <br/><br/> 열어둔 CMI에 **node myfirst.js**와 같이 입력한 뒤 Enter 키를 누르면 위에서 만든 파일이 실행됩니다.
![nodejs_start](./img/img2.png)

이제 다른 컴퓨터에서 내 컴퓨터로 접속할 수 있습니다. 이를 서버가 동작한다고 말합니다.<br/><br/>만약 다른 사용자가 8080 포트를 사용해서 접속한다면, 'Hello World'라는 'myfirst.js'파일에서 설정한 텍스트를 볼 수 있습니다.<br/><br/>인터넷 브라우저를 시작하고 http://localhost:8080 으로 접속해보세요!

# what is a Module in Node.js
Module은 Javascript의 라이브러리라고 생각할 수 있습니다.<br/>함수들의 집합이며 필요할 경우 내 파일에 포함시킬 수 있습니다.

## Built-in Modules
Node.js는 기본적으로 포함하고 있는 Module들이 있습니다. 기본적으로 포함된 모듈들을 살펴보고 싶다면 [Built-in Modules](https://www.w3schools.com/nodejs/ref_modules.asp) 이곳에서 볼 수 있습니다.

## Include Modules
기본적으로 포하됨 모듈들을 Include 하고 싶다면, **require()**함수를 사용해서 include할 수 있습니다.
```js
var http = require('http');
```
위와 같은 코드를 작성하는 순간 **http** 라는 Module에 접근할 수 있습니다. 그리고 이를 활용해 서버를 만들 수 있습니다.
```js
http.createServer(function(req,res){
    res.writeHead(200, {'Content-Type':'text/html'});
    res.end('Hello World');
}).listen(8080);
```

## Create Your Own Modules
위와같이 이미 있는 모듈들을 사용할 수도 있지만 새로운 모듈들도 만들수 있습니다. 그리고 이렇게 만들어진 것들을 쉽게 내 프로그램에 포함시킬 수 있습니다.<br/>밑의 코드는 모듈을 만들고 현재의 날짜와 시간을 반환할 수 있는 코드입니다.
```js
exports.myDateTime = function(){
    return Date();
};
```
**exports**키워드를 사용해서 properties와 methods를 만들고 밖에서도 이 모듈을 사용할 수 있도록 할 수 있습니다.<br/>위와 같이 작성했다면 이 코드를 'myfirstmodule.js'로 저장해주세요.

## Inclue Your Own Module
모듈을 만들었으니 이제 모듈을 프로그램에 include할 수 있습니다.
```js
// demo_module.js
var http = require('http');
var dt = require('./myfirstmodule.js');

http.createServer(function(req,res){
    res.writeHead(200, {'Content-Type':'text/html'});
    res.write("The date and time are currently: " + dt.myDateTime());
    res.end();
}).listen(8080);
```
> 위의 설명을 그대로 따라왔다면 CMI에서는 아무것도 입력되지 않습니다. 이는 서버가 실행중임을 뜻합니다. 이때 서버를 종료하려면 [Ctrl + C]를 눌러 종료할 수 있습니다.

위 코드에서 **./**는 현재 디렉토리를 나타냅니다 .따라서 './myfirstmodule.js'는 현재 폴더에서 myfirstmodule.js를 지시합니다. 이를 상대경로라고 합니다.<br/> 위 파일을 'demo_module.js'로 저장해주세요. 그리고 위에서와 같이 다음의 명령어로 서버를 실행합니다.
![result](img/img5.png)<br/>
이를 확인하기 위해서 [local](http://localhost:8080) 으로 접속해봅시다. 새로고침을 누르면 계속해서 시간이 바뀌는 것을 볼 수 있습니다. 이렇게 페이지가 시간과 장소 그리고 환경에 따라 변하는 페이지를 동적페이지라 말합니다.

# Node.js HTTP Module
## The Built-in HTTP Module
Node.js는 HTTP라고 불리는 기본적으로 포함된 모듈을 가지고 있습니다. 이는 데이터를 Hyper Text Transfer Protocol(HTTP)를 통해 데이터를 전달할 수 있도록 해줍니다. 이전에 살펴본 것과 같이 HTTP 모듈을 사용하기 위해서는 **require()**함수가 필요하며 다음과 같이 할 수 있습니다.
```js
var http = require('http');
```

## Node.js as a Web Server
HTTP 모듈을 통해 클라이언트에게 응답하고 특정한 서버 포트에 응답하는 HTTP 서버를 만들 수 있습니다. <br/> **createServer()** 함수를 써서 말입니다.
```js
var http = require('http');

//server 오브젝트를 만듦.
http = serverCreate(function(req,res){
    res.write('Hello World'); // 클라이언트에게 응답할 내용을 작성
    res.end(); //응답 끝을 알림
}).listen(8080); // 특정 포트(8080)를 listen 하도록 설정
```
**http.createServer()** 함수를 통해 8080포트로 접속할 수 있도록 해줍니다.<br/>위의 코드를 'demo_http.js'로 저장하고 실행해 봅시다.
```bash
> node demo.http.js
```
그리고 [local](http://localhost:8080) 으로 접속해서 서버가 정상적으로 작동하는지 확인해 봅시다.

## Add an HTTP Header
만약 HTTP를 사용해서 응답받은 결과를 HTML 출력하고 싶다면, HTTP 헤더를 설정해야 합니다.
```js
var http = require('http');

http.createServer(function(req, res){
    res.writeHead(200, {'Content-Type':'text/html'});
    res.write("Hello World");
    res.end();
}).listen(8080);
```
res.writeHead의 첫번째 Argument의 200은 '모든 것이 정상적이다' 를 뜻합니다. 두번째 Argument는 http 오브젝트의 Header를 설정하는 것입니다.

## Read The Query String
**http.createServer()**를 통해 전달되는 함수는 req argument를 가집니다. 이는 클라이언트로 부터 요청된 것을 말하며, 오브젝트입니다.(http.IncommingMessage object).<br/>이 오브젝트는 'url'이라고 불리어지는 property를 가지고 있으며 이는 Domain 뒤에 있는 url을 가져옵니다. 예를들어(https:www.naver.com/*pricture*)에서 picture 부분을 말합니다.

```js
// demo_http_url.js
var http = require('http');

http.createServer(function(req,res){
    res.writeHead(200 ,{'Content-Type':'text/html'});
    res.write(req.url);
    res.end();
}).listen(8080);
```
위 코드를 'demo_http_url.js'로 저장하고 파일을 실행해 봅시다.
```bash
> node demo_http_url.js
```
그리고 이를 한번 확인해 봅시다[Move_local](http://localhost:8080/123456789) 그리고 도메인뒤 **/** 의 숫자를 자신의 이름 또는 원하는 것을 입력하고 Enter 키를 누르면 페이지의 내용이 바뀌는 것을 볼 수 있습니다.
> 한글은 유니코드로 변환되어 출력됩니다.

## Split the Query String
URL 모듈을 활용해서 쉽게 Query String을 자를 수 있습니다.
```js
//http 객체 include
var http = require('http');
//url 객체 include
var url = require('url');

//서버 생성
http.createServer(function(req,res){
    res.writeHead(200, {'Content-Type':'text/html'}); // 헤더 설정
    var q = url.parse(req.url,true).query; //url 자르기
    console.log(q); // q 출력 확인 페이지와 관계없이 콘솔에 출력됨
    var txt = q.year + " " + q.month; //url을 통해 넘어오는 변수 이름 year와 month를 txt 변수에 하나로 묶음
    res.end(txt); 
}).listen(8080);
```
위의 코드를 'demo_quertstring.js'라고 저장하고 실행해 봅시다.<br/>
http://localhost:8080/?year=2020&month=4 <br/>위의 URL을 조금 살펴보면 도메인뒤 **?**는 '이제부터 변수 시작'을 의미합니다. 또한 **&(앰퍼샌드)**는 변수를 열거하기 위해 사용됩니다. 위의 QueryString의 꼴은 다음과 같습니다. 
```
[도메인]/?[변수이름]=[변수값]& ...
```