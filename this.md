---
description: 자바스크립트의 트릭인 this키워드의 사용 방법에 대해서 알아보겠습니다.
---

# 개념 정립 - this

### This 키워드란 ?

자바스크립트에서 this 키워드는 다양한 방법으로 사용될 수 있습니다. 일반적으로 this 키워드는 부모를 가리키게 되어있습니다. 아무것도 없는 상태에서 this를 가리키게 된다면 window, 즉 아무것도 없는 글로벌한 곳을 가리킨다는 말이 되겠죠. 예시를 보여 드리겠습니다.

{% code-tabs %}
{% code-tabs-item title="thisExample1.js" %}
```javascript
console.log(this); // {}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

이 결과는 당연합니다. 지금의 this가 가리키는 곳은 어떤 클래스도 아니고, 단지 브라우저에는 window객체를 가리키는 것이고 nodejs환경에서는 window객체가 존재하지 않으니 빈 객체를 출력하게 되는 것 입니다. this키워드가 유용하게 사용되는 곳은 클래스와 객체내에서 사용될 때에 있습니다. 앞으로의 예제를 보면 this가 왜 필요한지 알게 되실 겁니다.

{% code-tabs %}
{% code-tabs-item title="thisExample2.js" %}
```javascript
const testObejct = {
  a: '12345',
  consoleA: function() {
    console.log(this.a);
  },
};

testObejct.consoleA(); // 12345

```
{% endcode-tabs-item %}
{% endcode-tabs %}

this는 부모를 가리킨다고 했었죠? 그렇기 때문에 이 this.a는 testObject에 있는 a를 출력하게 되는 것 입니다. **하지만 여기서 이렇게 이해하고 넘어가면 안 됩니다.** 다음 예제를 보시면 개념이 조금 헷갈릴 수도 있는데 지금 부분을 잘 학습 하셔야 리액트 공부를 본격적으로 하실 때에 부담이 없게 됩니다.

{% code-tabs %}
{% code-tabs-item title="thisExample3.js" %}
```javascript
const testObejct = {
  a: '12345',
  consoleA: function() {
    console.log(this.a);
  },
};

const globalConsoleA = testObejct.consoleA;
globalConsoleA(); // undefined

```
{% endcode-tabs-item %}
{% endcode-tabs %}

뭔가 이상합니다. 달라진건 메소드를 특정한 변수에 저장해두고 그 변수에 담겨진 함수를 실행시켰을 뿐인데 결과가 완벽하게 달라졌습니다. **this가 결정되는 시점은, this가 선언된 시점이 아닌 누가 실행하는 지에 따라서 결정된다는 것을 알아야 합니다.**

두 번째 예제에서의 this실행 시점은, testObejct의 객체인 consoleA로써 실행되었기에 this가 부모인 testObject를 가리킨 것이고, 세 번째 예제에서의 this 실행 시점은, 어떤 특정한 변수에 담겨졌기 때문에 더 이상 그 메소드에서 가리키는 this가 원래의 부모 객체인 testObject를 가리키지 않고 글로벌한 this를 가리키게 되는 것 입니다. 이것은 함수 말고도 클래스에서도 동일하게 작용합니다. 리액트에서는 이벤트에 메소드를 넘기기 때문에, 이벤트에서 실행이 될 때는 이미 this는 사라진 상태가 됩니다. _\(그래서 앞으로 리액트 강의에서는this를 강제로 선언 시점에 고정해 두는 메소드를 사용할 것 입니다.\)_

#### 해결 예제

{% code-tabs %}
{% code-tabs-item title="thisExampleSolve.js" %}
```javascript
const testObejct = {
  a: '12345',
  consoleA: function() {
    console.log(this.a);
  },
};

const globalConsoleA = testObejct.consoleA.bind(testObject);
globalConsoleA(); // 12345

```
{% endcode-tabs-item %}
{% endcode-tabs %}

.bind\(\) 문법은 this를 고정시킬 때 사용하는 방법입니다. 지금 보면 함수를 넘길 때에 bind\(testObject\)라는 것을 추가했는데, 이 의미는 저 함수가 가리키는 this는 항상 testObject를 가리키게 하라는 의미입니다. 이렇게 되면 this가 실종될 일이 없어지게 됩니다. 

같은 예제를 이번에는 클래스로 생성하고 클래스에서의 해결법까지 알아보도록 하겠습니다.

#### 클래스 예제

{% code-tabs %}
{% code-tabs-item title="thisExampleClass.js" %}
```javascript
class testClass {
  constructor() {
    this.a = '12345';
  }

  consoleA() {
    console.log(this.a);
  }
}

const testClassInstance = new testClass();
testClassInstance.consoleA(); // 12345

const globalConsoleA = testClassInstance.consoleA;
globalConsoleA(); // Error 심지어 에러까지 발생합니다.

```
{% endcode-tabs-item %}
{% endcode-tabs %}

객체에서의 해결법처럼, 클래스에서도 메소드를 넘겨줄 때에 bind문법을 사용하면 해결할 수 있습니다.

{% code-tabs %}
{% code-tabs-item title="thisExampleClass.js" %}
```javascript
class testClass {
  constructor() {
    this.a = '12345';
  }

  consoleA() {
    console.log(this.a);
  }
}

const testClassInstance = new testClass();
testClassInstance.consoleA(); // 12345

const globalConsoleA = testClassInstance.consoleA.bind(testClassInstance);
globalConsoleA(); // 12345

```
{% endcode-tabs-item %}
{% endcode-tabs %}

클래스 메소드도 어짜피 넘겨지면 함수로 취급되기에, bind문법을 사용해서 해결할 수 있습니다.

### 이번 수업에서 꼭 기억해야 할 것

**this는 선언 시점에서 결정되는 것이 아니고, 메소드/함수를 어떤 주체가 실행 하는지에 따라서 결정 됩니다.**

_**\(이를 무시할 수 있는 방법 중 하나는 bind를 사용해서 강제로 지정하는 방법이 있습니다.\)**_

