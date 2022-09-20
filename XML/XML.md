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
        
        ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/54ee5a60-29f9-4a9d-9cdb-d01b67ecd256/Untitled.png)
        
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
