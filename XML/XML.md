## XML (e**Xtensible Markup Language)**

### 개요 및 정의

- W3C에서 권장하는 다목적 마크업 언어
- XML은 저장하고 전달할 목적으로만 설계
    - HTML은 데이터를 표시하는데 목적을 두고 있음
- XML 태그는 사용자가 직접 정의할 수 있음
    - HTML은 태그가 미리 정의되어 있음
- Ex)
    - HTML에서는 CPU 2.83GHz 라는 데이터를 표기할 때, 데이터명, 데이터값, 데이터단위의 경계를 알 수 없음
    - XML을 통해 위의 경계 즉 데이터에 의미를 부여하는 메타데이터를 기술할 수 있음
    
    ```xml
    <dataname>CPU</dataname><datavalue>2.83</datavalue>
    ```
    

### 특징

- 다른 목적의 마크업 언어를 만드는 데 사용되는 다목적 마크업 언어
- 다른 시스템간에 다양한 종류의 데이터를 손쉽게 교환할 수 있도록 해줌
- 확장성이 좋음
    - 새로운 태그를 만들어 추가해도 계속해서 동작하기 때문
- 데이터를 보여주는 것이 아닌, 전달하고 저장하는 목적
- 텍스트 데이터 형식의 언어, 유니코드 문자로만 이루어짐

> 문서용 마크업 언어를 정의하기 위한 메타언어 - SGML 기반으로 만들어짐
> 

### 개념 구조

- 트리(tree) 형태의 계층 구조를 가짐
    - 루트(root) 요소부터 시작 → 각각의 자식(child) 요소로 연결됨
    - 모든 요소는 자신의 자식 요소를 가질 수 있음
        
        <img width="479" alt="image" src="https://user-images.githubusercontent.com/45925685/191250576-65889771-7c24-44f9-a29f-8f30d0ddca7a.png">

        
    - 부모 → 여러 개의 자식 요소를 가질 수 있음
    - 자식 → 단 하나의 부모 요소만 가질 수 있음
    - 형제 요소는 같은 트리 레벨(tree level)에 존재하는 요소
        - 같은 부모 요소를 가지는 자식 요소 간의 관계
    - 조상 요소는 부모를 포함해 계층적으로 요소 자신보다 상위에 존재하는 모든 요소
    - 자손 요소는 자식을 포함해 계층적으로 요소 자신보다 하위에 존재하는 모든 요소
- 모든 요소는 자신만의 텍스트 혹은 속성을 가질 수 있음

### 문서 구조

- 기본적인 XML 문서는 다음 예시와 같이 구성

```xml
<?xml version="1.0" encoding="UTF-8"?>
<shop city="서울" type="마트">
    <food>
        <name>귤</name>
        <sort>과일</sort>
        <cost>3000</cost>
    </food>
    <food>
        <name>상추</name>
        <sort>야채</sort>
        <cost>2000</cost>
    </food>
</shop>
```

- 최상단에 <xml> 태그로 XML 문서임을 명시

```xml
<?xml version="1.0" encoding="UTF-8"?>
```

- XML 문서에 단 하나만 존재하는 루트(root)요소 생성
    - 이 루트는 모든 요소의 조상 요소가 됨

```xml
<shop city="서울" type="마트">
```

- 루트 요소(<shop>)은 두 개의 <food> 요소를 자식 요소로 가짐

```xml
<shop city="서울" type="마트">
    <food>
        ...
    </food>
    <food>
        ...
    </food>
</shop>
```

- <food> 요소는 자식 요소로 <name>, <sort>, <cost> 총 3개의 자식 요소를 가짐

```xml
<food>
    <name>귤</name>
    <sort>과일</sort>
    <cost>3000</cost>
</food>
```

- 다른 <food> 또한 동일한 자식 요소 (텍스트는 다른)를 가지고 있음

```xml
<food>
    <name>상추</name>
    <sort>야채</sort>
    <cost>2000</cost>
</food>
```

### 문법

- XML 문서의 최상단은 <xml> 태그를 사용하여 XML 문서임을 명시
    - 이를 XML 프롤로그라고 함
    - <xml> 태그는 소문자 xml로만 사용
    - version - XML 문서에 사용된 XML의 버전
    - encoding - 문자셋(character set), 기본값은 UTF-8
    - standalone - 외부 DTD(Document Type Definition)와 같은 외부 소스 데이터에 의존하는 문서인지 여부를 XML 파서에게 알려주는 역할, 기본값은 no, yes면 외부 소스가 없다는 의미

```xml
<?xml version="XML문서버전" encoding="문자셋" standalone="yes|no"?>
```

- 모든 XML 요소는 종료 태그를 가져야함

```xml
HTML : <h1>XML
       <hr>
XML  : <h1>XML</h1>
       <hr />
```

- XML 태그는 대소문자를 구분

```xml
<lecture>이 요소는 lecture 요소입니다.</lecture>
<Lecture>이 요소는 Lecture 요소입니다.</Lecture>
```

- 시작 태그와 종료 태그의 대소문자는 같아야 함

```xml
<lecture>이 요소는 lecture 요소입니다.</lecture>
<Lecture>이 구문은 오류를 발생합니다.</lecture>
```

- 태그의 여닫는 순서가 지켜져야 함
    - 먼저 열린 태그는 자손 태그가 모두 닫힌 후에 닫힐 수 있음

```xml
<p><strong>이 구문은 오류를 발생합니다.</p></strong>
<p><strong>이 구문이 정확한 순서입니다.</strong></p>
```

- 속성값은 반드시 따옴표로 감싸야 함

```xml
<student name=홍길동>   // 오류가 발생함.
<student name="이순신"> // 정상적으로 동작함.
```

- 띄어쓰기를 구별하고 인식함

```xml
코드 : <p>띄   어 쓰    기</p>
HTML : 띄어쓰기
XML  : 띄   어 쓰    기
```

### XML 요소 문법

- 요소 - 시작 태그부터 종료 태그까지의 모든 것
- 요소의 문법
    - 태그 사이에 자신의 내용을 가질 수 있음
    - 어떤 내용도 가지지 않는 빈 요소(empty element)도 생성할 수 있음
        - 빈 요소는 자신만의 내용은 없지만, 요소에 대한 데이터를 저장할 수 있는 속성은 가질 수 있음

```xml
<요소이름 속성1="속성값" 속성2="속성값"... > 내용 </요소이름>

<요소이름 속성1="속성값" 속성2="속성값"... /> // 닫힘 태그를 따로 쓰지 않고, 열림 태그에서 /로 마무리
```

- 요소 이름의 작성 규칙
    1. XML 요소의 이름은 영문자, 숫자, 하이픈(-), 언더스코어(_, underscore)와 점(.)만을 사용하여 작성
    2. XML 요소의 이름은 영문자의 대소문자를 구분
    3. 반드시 영문자나 언더스코어(_)로 시작해야 하며, 공백을 포함할 수 없음
    4. 예약어인 xml, XML, Xml 등은 요소의 이름으로 사용할 수 없음
    5. 시작 태그의 이름과 종료 태그의 이름은 반드시 대소문자까지 동일해야 함

### XML 속성 문법

- 속성 - 요소에 대한 추가적인 정보 제공, 해당 요소의 특징을 정의
- XML 요소의 속성은 속성명=”속성값" 형태로 정의
    - 속성값은 반드시 따옴표로 감싸야 함
- 요소와 속성의 차이
    
    ```xml
    // name을 요소로 표현
    <student>
        <name>홍길동</name>
        <year>3</year>
        <major>컴퓨터공학</major>
    </student>
    
    // name을 속성으로 표현
    <student name="홍길동">
        <year>3</year>
        <major>컴퓨터공학</major>
    </student>
    ```
    
    - 정보 전달이라는 측면에서 두 방식 모두 완전히 같은 정보를 제공
    - 속성의 제약
        - 여러 개의 값을 가질 수 없음
        - 요소처럼 확장할 수 없음
        - XML 트리에 포함되지 않기 때문에, 다양한 용도로 활용할 수 없음
- 속성 이름의 작성 규칙
    - 속성의 이름은 하나의 요소 내에서 중복되어서는 안됨
    ex) `<student name=”홍길동" age="17" name="홍길은"` (x)
    - 속성값은 반드시 따옴표로 감싸야하지만, 작은따옴표와 큰따옴표의 차이는 없음

### XML 엔티티 (Entity)

- XML에서 미리 예약되어있는 5개의 기호
- 해당 기호에 대해서는 XML 파서에서 예약된 의미로 해석함
    
    <img width="516" alt="image" src="https://user-images.githubusercontent.com/45925685/191278878-5dee0ab0-923b-4f54-9ff9-1d6db60c5421.png">

    

### XML 예시

XML에 대한 예시 이해 - [https://www.youtube.com/watch?v=55FrHTNjTCc&ab_channel=얄팍한코딩사전](https://www.youtube.com/watch?v=55FrHTNjTCc&ab_channel=%EC%96%84%ED%8C%8D%ED%95%9C%EC%BD%94%EB%94%A9%EC%82%AC%EC%A0%84)

<img width="431" alt="image" src="https://user-images.githubusercontent.com/45925685/191279000-7583062f-fe1c-4142-bbb2-e3f01da9ddd0.png">


- XML은 태그 형식을 사용함
    - 웹과 유사한 방식. XML로 웹을 표시할 수 있도록 만든 것이 HTML

```xml
<shop> // 테이블 전체
	<name> // 상호
		돌준이네 치킨
	</name>
</shop>
```

- 줄바꿈과 들여쓰기는 개발자가 보기 편하도록 구분해둔 것
    - parse는 태그를 구분점으로 구문을 이해하기 때문에 한 줄로 Minify 해도 동일하게 이해할 수 있음
    
    ```xml
    <shop><name>돌준이네 치킨</name></shop>
    ```
    
- XML의 각 태그들은 다양한 형태로 구성
    - 태그 단일로 존재
    - 시작과 종료 태그로 존재
        - 태그명이 각 데이터의 항목명이 되고, 시작과 종료 사이에 내용(데이터)가 들어감
        - 내용은 순수 단일 값이 들어갈 수도 있고, 하위에 새로운 태그명이 들어갈 수도 있음
    
    ```xml
    // 태그 단일
    <shop>
    
    // 태그 시작과 종료
    <shop>
    </shop>
    
    // 태그 시작과 종료 사이의 단일 값
    <name>
    	퍼피
    </name>
    
    // 태그 시작과 종료 사이의 다른 태그
    <shop>
    	<owner>
    		원태영
    	</owner>
    <shop>
    ```
    
- XML 문서의 최상단에는 버전과 인코딩 정보가 위치함

```xml
<?xml version="1.0" encoding="UTF-8">
```

### 마크업 언어

- 태그를 이용하여 데이터의 구조를 기술하는 언어
- 가장 흔하게 접할 수 있는 마크업 언어로 HTML이 있음
