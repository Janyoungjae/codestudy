# jQuery .attr()과 .prop()의 차이
***
## 1. 바뀐 시기
2011년 5월 3일 jQuery 1.6버전에서 .attr()에서 같이하던 처리를 .attr()와 .prop()로 나누었다.
1.6버전에서 많은 혼란이 있어서 1.6.1에서는 .attr()을 예전처럼 움직일 수 있도록 다시 수정되었다.~~하지만 1.6.1도 불완전한것 같습니다~~
<br>
[jQuery 1.6](http://blog.jquery.com/2011/05/03/jquery-16-released/) 2011년 5월 3일, [jQuery 1.6.1](http://blog.jquery.com/2011/05/12/jquery-1-6-1-released/) 2011년 5월 12일
### .attr()과 .prop()를 나눈이유
1. 원래 따로해야할 문제였다.
2. 같이 사용하는 문제로 버그가 많아져버렸다.
3. JavaScript로서는 .attr()과 .prop()는 다른것이기 때문이다.
***
## 2. .attr()과 .prop()의 다른 점
둘의 차이는 속성과 프로퍼티를 각각 취급하는 API이다.
>.attr()는HTML의속성을 취급을 하고, .prop()는JavaScript프로파티을 취급한다.

여기에서 혼란하는 이유는 속성과 프로파티는 "같지만 다른것"이라는 것이다.<br>
예를 들면

    <input type="checkbox" checked="checked" id="test">
    <script>
      var $checkbox = $("#test");
      console.log("attr : "+$checkbox.attr('checked'));
      console.log("prop : "+$checkbox.prop('checked'));
    </script>

의 체크박스의 체크가 되었을 때의 결과는 아래와 같다.

    attr : checked
    prop : true

체크박스의 체크가 해제 되었을 때의 결과는

    attr : checked
    prop : false

.attr()이 변하지 않는다 그러므로, input이 체크가 되어있는지 알고 싶으면, .attr()보단 .prop()을 사용하면 된다.<br>
"checked" 속성은 기능관련 속성이라 .prop() 함수에서는 true/false로 출력을 시켜준다.<br>
이 외에 각 속성들의 결과값을 가져오면 html의 id와 class값은 똑같이 가져온다.
***
## 3. 속성 변경 방법
$("").attr("속성명","적용하고자하는값") / $("").prop("속성명","적용하고자하는값")
둘 다 똑같으니 코드를 써서 이해를 해보면

    <input type="checkbox" id=test>
체크가 안된 이것을 checked의 값을 true로 바꾸고 싶으면 아래와 같이 코드를 추가하면

    $(function(){
        $("#test").prop("checked",true);
    })

체크박스가 체크가 되어 화면에 출력된 것을 확인 할 수 있습니다.

***
## 4. .attr()과 .prop()를 구분하는 방법
구분하는 간단한 방법은 attr()은 html 속성을 다루고 prop()는 javascript의 값을 다룬다.
