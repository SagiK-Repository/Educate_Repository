문서정보 : 2022.08.20. 작성, 작성자 [@SAgiKPJH](https://github.com/SAgiKPJH)

# **JSON**

-  JavaScript Object Notation(JSON)은 데이터 교환 포맷으로써, 인터넷에서 자료를 주고 받을 때 그 자료를 표현하는 방법으로 알려진 개방형 표준 포맷이다.
- 인간이 읽을 수 있는 문서이고, 코딩이 적게 필요하며, 처리속도가 빠른 경량언어이다.
- JSON은 상대적으로 쉽게 읽고 작성할 수 있고, 소프트웨어에서 파싱 및 생성하기도 쉽다.
- 자료의 종류에 큰 제한은 없으며, 프로그램의 변수값을 표현하는 데 적합하다.
- 종종 구조화된 데이터를 직렬화해 이를 네트워크에서 교환할 때(보통 서버와 웹 애플리케이션 간) 사용된다.
- 자바스크립트의 객체표기법으로부터 파생되어 독립된 언어로, 다른 언어와 호환성이 쉽다.
- JSON은 4가지 구조를 갖는다.
   1. JSON 데이터는 이름과 값의 쌍으로 이루어집니다.
   2. JSON 데이터는 쉼표(,)로 나열됩니다.
   3. 객체(object)는 중괄호({})로 둘러쌓아 표현합니다.
   4. 배열(array)은 대괄호([])로 둘러쌓아 표현합니다.

<br>

### JSON 구성
- JSON에서는 데이터의 값으로 사용할 수 있는 다양한 타입을 제공하고 있다.
- JSON에서 제공하는 기본 타입은 다음과 같습니다.
1. 숫자(number)
2. 문자열(string)
3. 불리언(boolean)
4. 객체(object)
5. 배열(array)
6. null

<br>

#### 1. 숫자(number)
```json
{
    "age": 1
}
{
    "weight": 2.14
}
{
    "size": 5.8426e+2
}
```
#### 2. 문자열
```json
{
    "name": "식빵"
}
```
이스케이프 시퀀스 | 설명
-- | --
\b | 백스페이스
\f | 폼 피드(form feed)
\n | 개행
\r | 캐리지 리턴(carriage return)
\t | 탭(tab)
\\" | 큰따옴표
\\/ | 슬래시
\\\ | 역슬래시
\uHHHH | 16진수 네 자리로 표현된 유니코드 문자
```json
{
    "comment": "안녕하세요. \"식빵\" 입니다."
}
```
#### 3. 불리언(boolean)
```json
{
    "name": "식빵",
    "lunch": true
}
```
#### 4. 객체(object)
- 객체 안의 객체도 가능하다.
```json
{
    "name": "식빵",
    "family": "웰시코기",
    "age": 1,
    "weight": 2.14
}
{
    "dog": {
        "name": "식빵",
        "family": "웰시코기",
        "age": 1,
        "weight": 2.14,
        "owner": {
            "ownerName": "홍길동",
            "phone": "01012345678"
        }
    }
}
```

#### 5. 배열(array)
- 객체를 배열의 요소로 가질 수 있다.
```json
{
    "dog": [
        "웰시코기",
        "포메라니안",
        "푸들"
    ]
}
{
    "dog": [
        "웰시코기",
        "포메라니안",
        "푸들",
        {
            "ownerName": "홍길동",
            "phone": "01012345678"
        }
    ]
}
```
#### 6. null
- 항상 소문자로 표기한다.
- 아무겂도 없는 빈 값이다.
```json
{
    "id": 1,
    "name": null
}
```

#### 기타
- JSON을 활용해 정보에 대한 검증과 더불어 값의 크기 또는 범위를 감지할 수 있도록 구성할 수 있다.
- 이는 JSON의 고급문법으로, 논리계산도 다룰 수 있다.  
- 예) 해당 데이터가 숫자이면서 3의 배수이거나, 아니면 숫자이면서 4의 배수인지를 검사하는 예제
```json
{
    "oneOf": [
        { "type": "number", "multipleOf": 3 },
        { "type": "number", "multipleOf": 4 }
    ]
}
```
- 예) 다음 예제는 해당 데이터가 문자가 아닌지를 검사하는 예제
```json
{
    "not": {
        "type": "string"
    }
}
```
- 예) 배열이 중복되는지 검사하는 예제
```json
{
    "type": "array",
    "uniqueItems": true
}
```


<br><br><br>

# 참조
- json 정보
  - https://ko.wikipedia.org/wiki/JSON
  - https://www.oracle.com/kr/database/what-is-json/
