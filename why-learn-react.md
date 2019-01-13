---
description: 왜 리액트를 배우는지 알아봅시다.
---

# 1강 - 리액트를 왜 배우니 ?

### 많은 개발자들이 왜 리액트를 사용할까요 ? 단순히 인기가 있어서 ? 

우리는 왜 현재 프론트 엔드 진영에서 많은 라이브러리와 프레임워크들이 Jquery로만 이루어진 기존 사이트들을 탈피하려고 하는지 알아볼 필요가 있습니다. 

사실, 일반적인 웹 사이트 같은 경우에는 프론트엔드 라이브러리 자체가 필요 없는 경우도 있습니다. 단순히 Jquery  + HTML + CSS만을 이용해서 프론트엔드를 구성할 수도 있습니다. 

Jquery 까지 필요가 없을 수도 있습니다. 정적 페이지\(블로그 글, 인터넷 기사\) 같은 경우에는 JS가 필요없을 수도 있습니다. 

그런데 요즘 웹은, 단순히 정적 페이지 만을 보여주면 되는 옛날의 웹이 더이상 아닙니다. 웹어플리케이션 이라고 불릴 정도로 웹이 정말 커지고 다양하게 변화했습니다.

JS를 이용해서 웹에 동적인 효과를 넣는 것 부터 시작해서, 실시간 통신, VR, 그래픽 게임을 만들 수도 있죠. 그런데 이러한 것들을 전부 Jquery 하나로 만든다고 생각해 보십시오. 지금의 방식을 고수한다면, 디버깅도 어렵고 수정도 어려운 코드를 양산하게 될 것입니다.

```markup
<div>
    <div id="count-container-1">
        <div>
            <span id="number-1">0</span>
        </div>
        <div>    
            <button id="up-1">Count up !</button>
            <button id="down-1">Count down !</button>
        </div>
    </div>
    <div id="count-container-2">
        <div>
            <span id="number-2">0</span>
        </div>
        <div>
            <button id="up-2">Count up !</button>
            <button id="down-2">Count down !</button>
        </div>
    </div>
</div>
```

```javascript
let numberOne = 0;
const numberOneElement = document.getElementById('number-1');
const increaseOneButton = document.getElementById('up-1');
const decreaseOneButton = document.getElementById('down-1');

btnIncreaseOne.onclick = function() {
  numberOne++;
  numberOneElement.innerText = numberOne;
}

btnDecreaseOne.onclick = function() {
  numberOne--;
  elNumberOne.innerText = numberOne;
}

let numberTwo = 0;
var elNumberTwo = document.getElementById('number-2');
var btnIncreaseTwo = document.getElementById('up-2');
var btnDecreaseTwo = document.getElementById('down-2');

btnIncreaseTwo.onclick = function() {
  numberTwo++;
  elNumberTwo.innerText = numberTwo;
}

btnDecreaseTwo.onclick = function() {
  numberTwo--;
  elNumberTwo.innerText = numberTwo;
}
```

지금 보시는 코드의 예제가 좀 극단적이긴 합니다만, Jquery를 이용해 웹을 제작할 경우, 수많은 데이터를 관리하기 위해 DOM에 있는 element를 선택해 가져오고, 이런식으로 변경하게 될 것입니다.

직접적으로 DOM조작을 하는 행위는 위험한 행위가 될 수 있습니다.

1. DOM 자체는 느리지 않습니다. 하지만, 그것을 변경한 후 재 렌더링 해 레이아웃을 다시 그리는 경우 DOM은 느려집니다. 특히, 다수의 DOM을 업데이트 하는 경우 DOM의 렌더링 퍼포먼스는 많이 내려갈 것 입니다. DOM은 한번에 전부를 그리는 행동을 빨리 할 수 있지만 특정 element를 선택해서 업데이트 하거나 변경하거나 하는 행동을 하는 것은 느립니다. \(이것은 DOM의 구조가 Tree 구조 때문이기도 합니다\)
2. InnerHTML을 이용해서 새로운 태그를 생성하거나 넣어줘야 하는 경우, DOM은 이것을 HTML로 재생성 하고 DOM 트리가 reflow\(업데이트\) 되기 때문에 굉장히 느려집니다.
3. 숙련된 개발자가 아니고서야 DOM 조작을 효율적으로 추상화 해서 처리하는 것은 힘듭니다. \(CSS로 해결할 수 있는 일을 JS를 쓰는 행위\)

또한 HTML이 커지고 다루어야 하는 데이터가 많아질 수록 JS 코드도 날로 증가하게 되는데, 기존 Jquery를 이용한 개발 방식으로는 프론트엔드 개발자들이 같은 코드를 공유하면서 개발하기 때문에 불편하고, Git 과 같은 프로그램을 이용할 경우 서로의 변경 내용이 꼬이기 쉽습니다. 물론, 서로의 개발 파트를 적절히 분배하고 개발한다면 해결할 수 있는 문제이겠지만, 여젼히 번거롭습니다.



### 리액트는 지금까지 우리가 느꼈던 문제의 해결책이 될 수 있습니다.

* 가상 돔의 사용으로 DOM 업데이트 최적화

리액트는 개발자들이 DOM 업데이트를 위해서 하는 최적화 행위를 가상 돔을 만들어 비교하고 DOM을 추상화 하여 필요한 부분만 다시 그리는 방식으로 개발자들이 DOM 업데이트를 오용하는 일을 피했습니다.  
[https://youtu.be/BYbgopx44vo](https://youtu.be/BYbgopx44vo)

* 컴포넌트 기반 

컴포넌트 기반인 리액트는 특정 기능을 구현하거나 특정 화면을 구현할 때 그 화면을 구성하는 일에만 집중할 수 있게 해 줍니다.

* 생태계

리액트의 생태계는 여타 다른 라이브러리, 프레임워크 커뮤니티보다 활발합니다. 단순 View 만을 관리하는 리액트가 프레임워크처럼 사람들이 사용할 수 있을 정도입니다. 페이스북이 만들었고 주도하고 있으며, Airbnb, netflix같은 기업들이 리액트를 사용 중에 있습니다.



### 리액트로는 무엇을 할 수 있을까 ?

'리액트' 한 가지 라이브러리로는 우리가 기대하는 멋진 페이지들을 만들 수는 없습니다. 하지만 그런 멋진 사이트를 만들 때 리액트를 같이 활용하면 훨씬 구조화되어 있고 유지보수하기 쉬운 페이지를 만들 수 있습니다. 또ㄴ한, SPA인 리액트를 활용할 경우 프론트엔드 영역과 백엔드 영역이 완전히 분리되어 있기 때문에 개발 영역 분리가 가능해 집니다. \(CSR한정..\) 더군다나 리액트를 이용해서 만들어진 사이트는 정말 많습니다. \(Facebook, Netflix, Airbnb,  Naver D2, etc... \) 그렇기 때문에 다른 회사들은 어떻게 활용하는지 참고해 가면서 만들 수도 있습니다.



### 우리의 목표

혼자서 구글링을 통해 라이브러리를 찾고 공부가 가능한 정도의 실력을 가지는 것이 목표입니다.

리액트 공부의 끝은 없습니다. 단순이 React 라이브러리만 사용한다고 하면 리액트를 배울 필요가 없습니다. 복잡한 수식을 시각화 해서 보여줘야 한다던지, 실시간 통신을 통해서 알림을 띄우는 작업들을 하려면 다른 개발자들이 만들어 배포중인 라이브러리를 직접 찾고 사용해야 우리가 원했던 복잡하고 멋진 웹을 만들 수 있습니다.  사용자와 많은 인터렉션이 필요한 웹의 경우에는 Client Routing 라이브러리를 찾아서 공부 \(react-router\) 해야 할 것이고, 그래프를 띄워야 한다면 그래프를 띄우는 라이브러리를 공부해야 할 것 입니다. \(이건 다른 프레임워크 동일합니다\)

