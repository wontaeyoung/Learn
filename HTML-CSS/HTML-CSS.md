# **HTML**

- 웹사이트의 형태를 표시하기 위해 작성하는 마크업 언어
- 태그를 사용하여 컨텐츠의 형태를 구분
- HTML은 태그와 컨텐츠로 이루어진 엘레멘트의 조합으로 구성되어 있음
- 크게 head 영역과 body 영역으로 구별

## Head

- 문서에 대한 부가적인 요소들을 작성하는 파트
    - 문서에 대한 설명
    - 웹 페이지의 이름
    - Style 태그
        - Style 작성을 Head에 할 수는 있지만, 거의 모든 경우 별도의 CSS 파일로 분리해서 작성
    - 지원해야하는 인코더(언어)
    - 연결해야하는 소스코드 파일 (CSS 등)

## Body

- 웹 페이지에서 표시할 실제 콘텐츠를 담는 파트
- 텍스트, 박스, 리스트 등 실제 태그들이 작성되는 곳

## **Tag**

- HTML을 기술하기 위한 명령어의 집합
- < > 사이에 기술한 명령어로 태그를 결정
- 여는 태그와 닫는 태그로 구성
    - 태그에 따라 닫는 태그 없이 단독으로 사용하는 경우도 있음
- 태그에 적용하는 다양한 옵션은 모두 여는 태그에 기술
    - 닫는 태그는 옵션 적용범위의 끝을 표시하는 기능

## **Element**

- 형태를 나타내는 태그와 내용에 해당하는 컨텐츠를 합쳐서 지칭하는 말
- <여는 태그> 컨텐츠 <닫는 태그> 형태로 구성

## **Attribute**

- 엘레멘트의 속성을 의미
- 이미지의 사이즈, 글자의 색 등 추가적인 속성을 지정할 수 있음
    - K : img 태그의 src=이미지링크도 일종의 Attribute에 해당
- 속성명="속성값" 형태로 작성
- 다수의 Attribute를 작성할 때는 <tag 와 > 사이에 Attribute를 나열
    - K : 이미지의 크기 -> 이미지 링크 순으로 작성해도 되는 것으로 보아 나열 순서의 제한은 없는 것 같음
- style이라는 속성을 많이 사용함
    - 엘레멘트의 디자인을 결정하는 속성

## **Event**

- 웹 페이지 내에서 클릭, 스크롤 등 사용자 동작을 의미
- 이벤트를 인식하기 위한 코드를 Element에 작성해서 사용자 동작을 캐치할 수 있음
- 사용자 동작을 캐치하면 그에 따라 미리 작성해둔 코드를 호출하여 실행시킬 수 있음
    - 사용자 동작에는 클릭, 스크롤, 포커스(마우스 커서 올려두기) 등이 있음
    - Element마다 사용할 수 있는 이벤트의 종류가 달라짐

### **click event 예시**

- 버튼을 클릭 -> 버튼이 클릭되었음을 표시하는 팝업창 출력하는 코드
    - onclick 속성은 사용자가 버튼을 클릭했을 때 호출되는 코드

```swift
<button type="button" onclick="javascript:alert('button is clicked')">
  Button
</button>
```

# **CSS**

- 다수의 Element에 일괄적으로 디자인을 적용하기 위한 언어
    - 복잡하고 많은 엘레멘트로 구성된 페이지의 색상을 일괄적으로 변경하는 경우에 유용함
    - Ex) 네이버 메인 페이지에서 대표 색상인 연두색을 모두 다른 색상으로 변경하려면, 모든 엘레멘트의 색상을 하나씩 변경해야 함

## **CSS 사용**

- CSS는 Body가 아닌 Head 영역에서 style 태그 안에 구현함 (선언)
    - K : 다른 언어에서 변수나 함수 등을 미리 선언하고 이를 활용하는 것과 비슷한 개념인듯 함
- Element에서 class 속성에 css 클래스명을 넣어주면, 선언한 css의 디자인이 반영됨
- 다중 클래스를 적용할 때는 class="클래스명1 클래스명2 ..." 형식으로 사용
- head 영역에서 선언해도 사용 가능하지만 통상적으로 .css 파일 안에 클래스들을 선언함
    - .css 파일에서는 <style> 태그로 감싸지 않아도 됨
    - .css 파일에서 클래스 선언 시, html head에서는 작성을 통해 연결해야 함
        - [link rel 속성값 종류](http://www.tcpschool.com/html-tag-attrs/link-rel)

```swift
선언 형태 .클래스명 { 속성값 } - 선언 예시 .colorSet { color:green; } - 사용
형태
<p class="클래스명">- 사용 예시</p>
<p class="colorSet"></p>
```

# **Reference**

- [https://namu.wiki/w/HTML](https://namu.wiki/w/HTML)
- [https://www.youtube.com/watch?v=cb7VlXqFla4&t=982s](https://www.youtube.com/watch?v=cb7VlXqFla4&t=982s)
- [https://www.w3schools.com/html/default.asp](https://www.w3schools.com/html/default.asp)
