# DOM
## 1. DOM이란?
>DOM(Document Object Model)은 HTML 문서의 모든 요소에 접근하는 방법을 정의한 API이다. DOM 객체는 텍스트와 이미지, 하이퍼링크, 폼 엘리먼트 등의 각 문서 엘리먼트를 나타낸다. 자바스크립트 코드에서는 동적인 HTML을 만들어내기 위해 DOM 객체에 접근해서 조작할 수 있다. 여러 브라우저에서 HTML을 공통적으로 표현, 제어 할 수 있도록 공통적인 객체 모델을 만들려고 한 인터페이스이다.

***
## 2. DOM의 트리 구조
![DOM의 트리구조](http://chie.co.kr/150225/images/pic_htmltree.gif)
이 위에를 해석해보면

    <!DOCTYPE html>
    <html>
      <head>
        <meta charset="utf-8">
        <title>My title</title>
      </head>
      <body>
        <a href="#">My link</a>
        <h1>My header</h1>
      </body>
    </html>

이것과 같이 나오게 되고 이것은 XML과 동일하다.
>W3C DOM 에서는 HTML 문서를 XML로 바라본다. 즉 각 문서에 있는 태그들은 node(객체)가 있는 트리 구조로 해석해낼수있다고 가정하는 것이다. 각 태그들은 element noede(요소 노드) 와 text node(텍스트 노드)가 있다고 생각하며 각각의element node에 있는 속성 값들은 attirbute node로 인식한다.

***
## 3. DOM의 Level
지금의 DOM의 규격은 Level 2이다. 그러나 Level 3 규격도 현재 W3C의 권고안이다. Level은 총 3단계가 있다.
> 0. Level 0 DOM이 만들어지기 이전의 모든 벤더 종속적인 DOM을 포함한다. 예 : document.images, document.forms, document.layers, document.all.
단, 이것은 W3C에 의해 공식적으로 공개된 규격이 아니며, 표준화 이전에 있던 단계를 말한다.
> 1. Level 1 : DOM 문서에 대한 탐색과 조정
> 2. Level 2 : XML 명칭 공간 지원, 필터링된 뷰(view)와 DOM 이벤트.
>>DOM 이벤트란 DOM (문서 객체 모델) 이벤트 기반 프로그래밍 같은 언어 JavaScript , JScript, ECMAScript, VBScript 하고 자바는 다양한 등록 이벤트 핸들러 / 리스너 는 A 내부 요소 노드에 DOM의 트리 예를 들어 HTML , XHTML , XUL 및 SVG의 문서. 모델 웹 브라우저는 몇몇 중요한 차이가 있다. 이로 인해 호환성 문제가 발생했습니다. 이것을 방지하기 위해, 이벤트 모델은 표준화 된 것이 W3C의 DOM Level 2이다.
> 3. Level 3 : 단계 3
6가지 다른 규격으로 구성:
>>1. 코어 문서를 조작하고 접근하여 사용할 수 잇는 최소한의 인터페이스<br>
>> 2. 불러와서 저장(Load and Save) : XML 문서를 DOM 트리로 읽어오고 DOM트리를 XML 문서로 저장하기 위한 인터페이스<br>
>>3. XPath : 	DOM을 검색하고 편리한 간편한 표현식을 사용할 수 있게 한다.<br>
>> 4. 보기 및 초기화(formatting)<br>
>> 5. 요구사항<br>
>> 6. 유효 확인 : DOM 트리를 수정하고도 여전히 유효한 문서가 되도록하기 위한 메소드 정의
