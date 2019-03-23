---
description: Javascript의 문법 확장
---

# Babel

일반 자바스크립트 문법과 create-react-app에서 작동하는 문법은 조금 많이 다릅니다. 일단 모듈을 import하는 방식부터 다른데요. 한번 비교해 볼까요 ?

```text
import react from 'react'; // create-react-app에서 사용되는 문법
const react = require('react'); // node.js에서 현재 사용되는 import 문법
```

이 문법들 간의 차이가 보이실 겁니다. 첫번째 줄 코드는 nodejs상으로는 돌아가지 않습니다. 그러나, 두번째 줄과 첫번째 줄의 기능상 차이는 없습니다. 단순히 문법이 다른 것 뿐 하는 일은 같습니다. 그러나 nodejs의 기본 문법 명세인 commonjs 에서는 import 문법을 지원하지 않습니다.

### 그런데 나는 어떻게 실행을 시켰지?

리액트 개발을 CRA로 하신 분들이라면 이해가 되지 않을 수도 있습니다. 리액트에서 import 문법을 사용할 수 있었던 이유는 **Babel** 덕분입니다.

### 문법을 통일해 주는 Babel

_자바스크립트의 문법 업데이트가 빠른 만큼, 브라우저들은 문법을 추가하기에 급급하지만 그래도 Node.js는 잘 따라와주는 편 입니다. 하지만 기본 모듈 export, import 방식이 commonJS를 채택하고 있는지라 이 부분이 조금 불편하게 느껴질 수도 있습니다._

현재 자바스크립트는 1년마다, 아니 몇 개월마다 새로운 최신 문법이 추가되기도 하고 업데이트 되기도 합니다. 그러나 우리의 브라우저, nodejs 들은 문법이 새로 나올 때마다 바로바로 업데이트를 해 주지는 않습니다. nodeJS같은 경우에는 웬만한 문법을 지원하긴 하지만 그렇다고 해도 여전히 최신 문법을 자유롭게 사용할 수 있는 상황은 아닙니다. 그렇게 되면 최신 문법은 나오기만 하고 사용할 수 없는 상태가 되버리고 마는데요, 이런 문제를 해결해 줄 수 있는 것이 바로 Babel 입니다. 사실, 최신 문법은 기존 문법으로도 구현할 수 있습니다. 다만 표현 방법이 다를 뿐 입니다. import 문법 같은 경우에도, 사실 기존 문법으로 완벽 대체가 가능합니다.

{% code-tabs %}
{% code-tabs-item title="CommonJS and AMD" %}
```javascript
const a = [1, 2, 3, 4];

exports.a = a;

const a = [1, 2, 3, 4];

export { a };

```
{% endcode-tabs-item %}
{% endcode-tabs %}

### 그런데 우리는 왜 호환성도 좋지 않은 최신 문법을 사용할까요?

```javascript
class HelloEs6 {
    constructor() {
    }
    
    newMethod() {
        console.log('hello i am new method');
    }
}

var BeforeClass = (function () {
  function BeforeClass() {
  }

  BeforeClass.prototype.newMethod = function () {
    console.log('hello i am new method');
  };

  return BeforeClass;
}());

```

두 코드는 같은 기능을 하는 입니다. 그런데도 첫 번째 코드가 저에게는 유난히 눈에 더 잘 들어오네요. 아마 여러분들도 똑같이 느끼실 것 이라고 생각합니다. 나중에 유지보수를 하는 입장이나, 처음 자바스크립트를 접하는 입장일 때에는 첫 번째 코드가 더 이해하기 쉽고 좋은 것 같습니다.

또다른 이유는 당연히 Babel의 덕분이겠죠. 최신 문법으로 작성한 코드를 낮은 문법에서만 동작하는 코드로 변환시켜 브라우저나 서버에서 제대로 동작하게 도와줍니다. create-react-app에도 이러한 작업이 미리 되어있기 때문에 우리는 자바스크립트 최신 문법을 사용할 수 있었습니다.



