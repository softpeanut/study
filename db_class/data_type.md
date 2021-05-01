# 데이터형

### 중요성

각 데이터 마다 특징이 있고, 특징들 마다 맞는 데이터형, 데이터 길이가 있다.

만약 이름 컬럼의 길이가 CHAR(100)이라면 이름이 3글자인 사람이 오면 97바이트가 낭비된다.



게다가 조회할 때도 훨씬 느리다.

> char는 남는 공간을 빈 공간으로 채우기 때문이다.

### 기본 문자형

| 타입     | 최대 크기 | 기본 크기 | 특징               |
| -------- | --------- | --------- | ------------------ |
| char     | 2000      | 1         | 고정 길이          |
| nChar    | 2000      | 1         | 유니코드 문자형    |
| Varchar2 | 4000      | 생략 불가 | 가변길이           |
| Varchar  | 4000      | 생략 불가 | 가변 길이 유니코드 |

> 만약 CHAR(4)에 'ABC'를 넣고, WHERE에서 'ABC'로 검색하면 찾을 수 없다.
>
> 공백으로 채웠기 때문에, 'ABC '로 검색해야 결과가 나온다.

> 만약 고정 길이라면 CHAR를 사용하는게 좋다.
>
> VARCHAR2는 길이를 재설정 하는데 자원이 소모되기 때문이다.

### 기본 숫자형

| 타입         | 예                | 특징                                                         |
| ------------ | ----------------- | ------------------------------------------------------------ |
| NUMBER       |                   | 크기 제한이 없으면 38자리로 한다.                            |
| NUMBER(3)    | 123               | 정수 3자리                                                   |
| NUMBER(6,2)  | 1234.12           | 총 6자리, 소수점 이하 2자리.                                 |
| NUMBER(6,-2) | 123478.56 -> 1200 | 8자리중 정수 2자리를 0으로 변경. 소수점은 버리고, 뒤의 2개는 반올림 된다. |
| FLOAT(128)   | 2121              | NUMBER의 하위 타입                                           |

> NUMBER에서 속성을 2개 지정헀을 때, 저장 가능 정수 자릿수는 `앞의 숫자 - 뒤의 숫자`다.

만약 NUMBER(3,4)처럼 사용하면 0.0121 처럼 소수점 아래로 내려가야 사용할 수 있다.

### 날짜형

| 타입      | 특징                                                         |
| --------- | ------------------------------------------------------------ |
| DATE      | BC 4712년부터 9999년 12월 31일까지 입력 가능.<br />연,월,일,시,분,초 까지 입력 가능 |
| TIMESTAMP | 연,월,일,시,분,초,밀리초 까지 입력 가능                      |

TIMESTAMP는 TIMEZONE을 설정해 줘서 어떤 지역의 시간으로 저장할지 알 수 있다.

`SYSDATE`함수로 날짜를 가져올 수 있다.

성능 면에선 더 좋지만, 검색할 때 초 까지 모두 저장해야 한다.

> 만약 날짜 까지만 저장한다면 VARCHAR()를 사용한다.

날짜형을 사용하면 일자 연산이 가능하다.

즉 하루를 더하고 싶을 때, DATE형은 그냥 더하면 된다.

### LOB 타입

| 타입  | 설명                                                  |
| ----- | ----------------------------------------------------- |
| CLOB  | 문자형 대용량 객체로, 고정길이와 가변길이를 지원한다. |
| NCLOB | 유니코드를 지원하는 대용량 객체                       |
| BLOB  | 이진형 대용량 객체                                    |
| BFILE | 대용량 이진 파일에 대한 위치, 이름 저장               |

LOB란 Large OBject의 약자로, 큰 데이터를 저장할 수 있는 타입이다.

주로 그래픽, 사진 등을 비정형 데이터로 저장할 때 사용한다.

최대 4GB까지 저장할 수 있다.