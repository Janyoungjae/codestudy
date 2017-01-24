# 1. 이벤트 버블링이란?
html에서 해당 엘리먼트가 이벤트가 발생이 되었을때, 해당 요소로 시작해 상위 요소가 차례로 이벤트를 처리하는 방식 ~~반대는 캡처링~~<br>
![버블링](http://cfile9.uf.tistory.com/image/031E0240519346A407A1FD)<br>
Document에서 시작해 html body ...으로 내려가는 것을 캡처링이라고 한다.
이벤트를 발생시킨 DOM 객체를 타겟 객체라 하며, 타겟 객체에 이벤트를 발생시킨 이후 이벤트가 타겟 객체(현재의 <td>)의 부모로 전달되고 또 그 부모의 부모객체를 이어가며 다시 최상위 Document까지 이벤트가 전달되는 것이 버블링(bubbling)이다.
***
버블링을 알아보기 위해 자바스크립트 코드와 html코드를 작성 <br>

    <!DOCTYPE html>
    <html>

    <head>
        <meta charset="utf-8">
        <title></title>
        <script src="jquery.js"></script>
        <script type="text/javascript">
            $(function() {
                $("*").click(function(e) {
                    var current = this;
                    var target = e.target;
                    console.log('For ' + current.tagName + '#' + current.id + ' target is ' +
                        target.tagName + '#' + target.id);
                });
            });

        </script>
        <style media="screen">
            #div1 {
                background-color: yellow;
                margin: auto;
                text-align: center;
                padding: 100px;
                width: 500px;
            }

            #div2 {
                background-color: blue;
                margin: auto;
                padding: 70px;
                width: 300px;
            }

            #example {
                margin: auto;
                padding: 30px;
                width: 100px;
            }

        </style>
    </head>

    <body>
        <div id="div1">
            <div id="div2">
                <img id="example" src="https://scontent-icn1-1.xx.fbcdn.net/v/t1.0-1/c1.0.160.160/p160x160/15203159_566234323575868_6271724051605978211_n.jpg?oh=7850b969cf026abc97c25a58d0871a4b&oe=590D655A">
            </div>
        </div>
    </body>

    </html>

***
![실행결과](img.png)
<br>
console에서 보이는 결과와 같이 클릭 이벤트가 발생한 지점에서 시작하여 부모 객체로 점점씩 올라가는 결과가 나온다. 이것이 버블링!<br>
버블링의 단점이 있는데 이렇게 위로 올라가다보니까 부모 객체에서도 그 이벤트가 실행이되어서 같이 돌아간다.<br>
그래서  jQuery에서는 이를 방지하는 메소드를 제공한다.<br>
.stopPropagation()이라는 코드이다.

    <script type="text/javascript">
        $(function() {
            $("*").click(function(e) {
                e.stopPropagation();
                var current = this;
                var target = e.target;
                console.log('For ' + current.tagName + '#' + current.id + ' target is ' +
                    target.tagName + '#' + target.id);
            });
        });

    </script>

***
실행결과
![실행결과](img2.png)
이미지를 클릭 했을때 이미지만 이벤트가 발생하고,
부모객체는 더이상 영향이 받지않는다.
