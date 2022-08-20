문서정보 : 2022.08.20. (원본 2022.08.13.~19. 작성) 작성, 작성자 [@SAgiKPJH](https://github.com/SAgiKPJH)

# **HTTP**
- HTTP(HyperText Transfer Protocol)는 클라이언트와 서버간의 정보를 주고받을 수 있는 프로토콜이다.
- 프로토콜이란 `상호 간에 정의한 규칙`을 의미한다.
- 하이퍼텍스트라는 용어는 1965년 제너두 프로젝트에서 테드 넬슨이 만들었으며, 팀 버너스 리와 그의 팀은 CERN에서 HTML뿐 아니라 웹 브라우저 및 텍스트 기반 웹 브라우저 관련 기술과 더불어 오리지널 HTTP을 발명하였다.
- HTTP는 주로 HTML 문서를 주고 받는데 쓰인다.
- HTTP를 통해 전달되는 자료는 http:로 시작하는 URL(인터넷 주소)로 조회할 수 있다.

<br>

### 동작 방식
- 클라이언트와 서버 사이에 이루어지는 요청/응답(request/response) 프로토콜이다.
- 클라이언트와 서버 사이의 소통은 평문(ASCII) 메시지로 이루어진다.
- 클라이언트는 서버로 요청메시지를 전달하며 서버는 응답메시지를 보낸다.
- 요청 내용과 헤더 필드는 <CR><LF>로 끝나야 한다. (2바이트 CR LF ('\r\n'))
- 주로 TCP/IP 통신을 사용하고, HTTP/3 부터는 UDP를 사용하며, 80포트를 사용한다.

<br>

## 동작 예제
### 클라이언트 요청
```http
GET /restapi/v1.0 HTTP/1.1
Accept: application/json
Authorization: Bearer UExBMDFUMDRQV1MwMnzpdvtYYNWMSJ7CL8h0zM6q6a9ntw
```
### 서버 응답
```html
HTTP/1.1 200 OK
Date: Mon, 23 May 2005 22:38:34 GMT
Content-Type: text/html; charset=UTF-8
Content-Encoding: UTF-8
Content-Length: 138
Last-Modified: Wed, 08 Jan 2003 23:11:55 GMT
Server: Apache/1.3.3.7 (Unix) (Red-Hat/Linux)
ETag: "3f80f-1b6-3e1cb03b"
Accept-Ranges: bytes
Connection: close

<html>
<head>
  <title>An Example Page</title>
</head>
<body>
  Hello World, this is a very simple HTML document.
</body>
</html>
```

코드 | 내용
:--: | :-- 
GET | 존재하는 자원에 대한 요청
POST | 새로운 자원을 생성
PUT | 존재하는 자원에 대한 변경
DELETE | 존재하는 자원에 대한 삭제

<br>

### 응답코드
- 클라이언트가 서버에 접속하여 어떠한 요청을 하면, 서버는 세 자리 수로 된 응답 코드와 함께 응답한다.
- 대표적인 HTTP의 응답 코드는 다음과 같다.

코드 | 메시지 | 설명
:---: | :--: | :--
**1xx** | **Informational<br>(정보)** | **정보   교환.**
100 | Continue | 클라이언트로부터 일부 요청을   받았으니 나머지 요청 정보를 계속 보내주길 바람. <br>(HTTP 1.1에서 처음 등장)
101 | Switching   Protocols | 서버는   클라이언트의 요청대로 Upgrade 헤더를 따라 다른 프로토콜로 바꿀 것임.<br> (HTTP 1.1에서 처음 등장)
**2XX** | **Success<br>(성공)** | **데이터   전송이 성공적으로 이루어졌거나, 이해되었거나, 수락되었음.**
200 | OK | 오류   없이 전송 성공.
**3XX** | **Redirection<br>(방향   바꿈)** | **자료의   위치가 바뀌었음.**
**4XX** | **Client   Error<br>(클라이언트 오류)** | **클라이언트   측의 오류. 주소를 잘못 입력하였거나 요청이 잘못 되었음.**
**5XX** | **Server   Error<br>(서버 오류)** | **서버   측의 오류로 올바른 요청을 처리할 수 없음.**




<br><br><br>

  
  
# 참조
- HTTP 정보
  - https://ko.wikipedia.org/wiki/HTTP
  - https://joshua1988.github.io/web-development/http-part1/
