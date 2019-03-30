---
description: '''화살표 함수'' 에 관해서'
---

# Arrow function

### 새로운 문법인 화살표 함수가 생겼습니다!

기존 함수보다 훨씬 간편하게 사용할 수 있는 문법인 화살표 함수를 리액트에서는 적극적으로 활용합니다.

_+++ 리액트에서는 클래스 메소드를 화살표 함수의 형태로 선언하는 것도 가능합니다._

우선, 우리가 기존에 쓰던 함수를 예시로 작성해 보도록 하겠습니다.

{% code-tabs %}
{% code-tabs-item title="oldFunction.js" %}
```javascript
function oldFunction() {
    return '나는 옛날 함수입니다'
};

```
{% endcode-tabs-item %}
{% endcode-tabs %}

함수를 하나 선언하고 문자열을 리턴해 주었습니다. 이것을 새로운 문법인 화살표 함수로 바꾸어 볼까요?

{% code-tabs %}
{% code-tabs-item title="newFunction.js" %}
```javascript
const newFunction = () => {
    return '나는 새로운 함수입니다'
};

```
{% endcode-tabs-item %}
{% endcode-tabs %}

표현 방식이 다를 뿐, 둘은 같은 작업을 수행합니다. 다른 것은 화살표 함수에는 함수 이름을 설정할 수가 없다는 것이죠. 그래서 변수에 함수를 담는 형태가 됩니다. 그래서 화살표 함수 자체만을 얘기하자면 밑의 형태만을 얘기하는 것이 맞습니다.

{% code-tabs %}
{% code-tabs-item title="pure.js" %}
```javascript
() => {
    return '나는 새로운 함수입니다'
}

```
{% endcode-tabs-item %}
{% endcode-tabs %}

자바스크립트를 프로그래밍할때 콜백을 담는 형태에 함수를 담는 형태가 있는데, 그럴 때 화살표 함수를 사용하면 코드의 줄 수를 줄이면서 직관적인 프로그래밍을 할 수 있습니다.

### 더 짧게, 더 직관적으로, 더 편하게

이런 함수가 있다고 해도, 지금까지의 설명으로는 화살표 함수를 사용하는 것을 배울 필요가 없습니다. 이미 기존에 우리가 알고 있던 함수의 형태로도 충분히 프로그래밍을 잘 할수 있기 때문이죠. 그런데 왜 리액트나 앵귤러를 사용해서 SPA를 개발하는 프로그래머들은 최신 문법인 화살표 함수를 사용하는 걸까요? 그 이유는 아래에 있습니다.

{% code-tabs %}
{% code-tabs-item title="whyArrowFunction.js" %}
```javascript
function oldFunction() {
    return '나는 옛날 함수입니다'
};

const newFunction = () => '나는 새로운 함수입니다';

```
{% endcode-tabs-item %}
{% endcode-tabs %}

간단한 작업의 경우라면, 화살표 함수는 괄호를 사용하지 않은 채로 화살표 뒤에 반환해줄 값을 설정하게 되면, 그 값이 반환됩니다. 코드의 줄을 줄일 수 있을 뿐만 아니라 굉장히 이해하기 쉬운 코드가 됩니다. 훨씬 직관적이구요.

#### 객체를 리턴할때는 어떻게 하지?

객체 자체가 괄호에 쌓인 형태이기 때문에, 객체를 리턴하려면 기존 방식을 사용해야 하지만, ES6 화살표 함수는 이런 문제를 해결할 수 있는 기능을 이미 내장하고 있습니다.

{% code-tabs %}
{% code-tabs-item title="returnObject.js" %}
```javascript
// 괄호 안에 이상한 문법이 들어가 버렸습니다...!
const newFunctionWrong = () => { a: '나는객체요소' };

// 소괄호로 감싸게 되면 객체 자체를 리턴할 수가 있게 됩니다.
const newFunction = () => ({ a: '나는객체요소' });

```
{% endcode-tabs-item %}
{% endcode-tabs %}

리턴할 객체 위에 소괄호를 감싸면 객체 자체를 리턴할 수 있는 형태가 됩니다.

