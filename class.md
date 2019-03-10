---
description: 자바스크립트의 Class문법에 관한 내용입니다. 강의 시작 전 보시면 정말 좋습니다.
---

# 개념 정립 - Class

### 자바스크립트 클래스 강의

리액트를 배우기 위해서는 자바스크립트의 클래스 개념을 알고 가면 정말 좋습니다. _\(Java를 먼저 학습하고 실무에서 사용하고 계시는 개발자 분들이라면 30분 안에 모든 개념을 익히실 수도 있습니다.\)_

자바스크립트에서는 본래 Class문법이 존재하지 않았습니다. 그래서 다른 언어의 클래스 문법을 흉내내서 사용하는 기법을 사용했습니다. 아래가 예시입니다.

{% code-tabs %}
{% code-tabs-item title="pastClass.js" %}
```javascript
function pastClass (myName) {
    this.myName = myName;
    this.pastClass = 'pastClass';
} 
pastClass.prototype.getInfo = function() {
    return this.pastClass + ' ' + this.myName + ' ' + 'made by Lee';
};

const newClass = new pastClass('Lee jihoon');
console.log(newClass.getInfo()); // 'passClass Lee jihoon made by Lee'
```
{% endcode-tabs-item %}
{% endcode-tabs %}

pastClass의 함수 선언문이 일반적인 클래스의 생성자와 같은 역할을 한다고 보시면 됩니다. 또한 메소드를 추가하는 방식은 prototype에 함수를 붙이는 방식으로 메소드를 추가했습니다. 지금 만들어진 예제를 새로운 자바스크립트의 클래스 문법을 사용하면 다음과 같이 변하게 됩니다.

{% code-tabs %}
{% code-tabs-item title="newClass.js" %}
```javascript
class pastClass {
    constructor(myName) {
        this.myName = myName;
        this.pastClass = 'pastClass';
    }
    
    getInfo() {
        return this.pastClass + ' ' + this.myName + ' ' + 'made by Lee';
    }
}
const newClass = new pastClass('Lee jihoon');
console.log(newClass.getInfo()); // 'passClass Lee jihoon made by Lee'
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### 클래스 문법에 대해 자세히 알아보기

#### 생성자

제가 위에서 '생성자' 라는 단어를 사용 했었습니다. 생성자란 클래스가 생겨날 때에 첫 번째로 실행되는 메소드 입니다. 클래스 내에 생성자를 넣어도 되고 넣지 않아도 됩니다. 자바스크립트의 클래스는 생성자를 선언하지 않으면 자동으로 빈 생성자가 호출되는 형식으로 만들어져 있습니다. 모든 클래스가 new 를 통해서 인스턴스가 생성되었을 시점에는 무조건 생성자가 호출됩니다. _\(new를 통해서 클래스 한개가 만들어 지게 되면 그걸 인스턴스라 칭하겠습니다.\)_

#### 클래스 내부에서는 선언이 불가능 합니다.

{% code-tabs %}
{% code-tabs-item title="noDeclaration.js \(error\)" %}
```javascript
class pastClass {
    myName = '';
    pastClass = '';
    
    constructor(myName) {
        this.myName = myName;
        this.pastClass = 'pastClass';
    }
    
    getInfo() {
        return this.pastClass + ' ' + this.myName + ' ' + 'made by Lee';
    }
}
const newClass = new pastClass('Lee jihoon');
console.log(newClass.getInfo()); // 'passClass Lee jihoon made by Lee'
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**지금의 예제는 node.js 환경에서 실행 시 오류가 발생하게 됩니다.**

위의 클래스 예제와 다른 점이라면 클래스 내부에 기본값을 선언해 둔다는 점인데, 기본적인 node.js 환경에서는 클래스 내부에 값을 선언하는 문법은 사용이 불가능 합니다. _다만 우리가 앞으로 배울 CRA보일러 플레이트에서는 사용할 수 있는데, 그 이유는 최신 문법을 리액트가 자동으로 사용가능하도록 babel을 이용해 처리를 해 주기 때문입니다._

#### extends를 이용한 클래스 확장

이 부분이 바로 자바스크립트에서 새로운 클래스 문법을 사용할 때의 이점이라고 볼 수 있겠네요. 다만 조금 개념이 어렵습니다. 두 개의 클래스를 만들고 상속하는 형태로 만들어 보도록 하겠습니다.

{% code-tabs %}
{% code-tabs-item title="extendExample.js" %}
```javascript
class pastClass {
  constructor(myName) {
    this.myName = myName;
    this.pastClass = 'pastClass';
  }

  getInfo() {
    return this.pastClass + ' ' + this.myName + ' ' + 'made by Lee';
  }
}

class extendsClass extends pastClass {
  // 부모 생성자에게 전해줄 myName
  constructor(myName) {
    // super를 이용해서 부모 생성자 호출, 생성자에게 필요한 myName도 넘겨줍니다.
    // super는 부모 생성자를 호출할 수 있는 메소드 입니다.
    // 자식 클래스에서 super를 호출하지 않을 경우 오류가 발생합니다.
    // 하지만, 자식 클래스에서 생성자 자체를 선언하지 않았다면 오류는 발생하지 않습니다.
    super(myName);
  }

  // 부모 클래스의 메소드를 재 선언 하게 되면 자동으로 덮어씌워집니다.
  getInfo() {
    console.log(this.pastClass);
    return 'This is extends Class !';
  }
}

const testValue = new extendsClass();
console.log(testValue.getInfo()); // 'This is extends Class !'

```
{% endcode-tabs-item %}
{% endcode-tabs %}

뭔가 갑자기 복잡해진 것 같은데, 전혀 복잡하지 않습니다. 코드 실행 순서를 정리해 드리겠습니다.

1. 두 개의 클래스가 정의됨
2. testValue라는 곳에 extendsClass인스턴스가 생성
3. testValue의 getInfo메소드의 리턴값을 출력함

이 과정에서 어떻게 리턴값이 'This is extends Class !'가 나왔을까요 ? 그리고 super키워드는 처음 보는데 뭐죠? 와 같은 의문이 생겼을 것입니다. 어렵지 않습니다.

#### super 키워드는 부모의 생성자를 호출하기 위해 존재합니다.

자바스크립트의 문법에서, 클래스를 확장 받았을 때 _\(extendsClass는 자식 클래스가 되고, pastClass는 부모 클래스가 됩니다.\),_  **자식 클래스의 생성자에서는 반드시 부모 생성자를 호출 시켜야 합니다. 그렇지 않게 되면 오류가 발생합니다.** 그 역할을 super 키워드가 하는것이고, super 키워드에 myName 값을 넘기는데, 이건 마치 클래스를 선언할 때 생성자에 넘기는 값과 동일하게 부모 생성자의 인자로 들어가게 됩니다.

#### 자식 클래스에서 부모 클래스에 정의되어있는 메소드를 덮어씌울 수 있습니다.

자실 클래스와 부모 클래스 동일하게 getInfo라는 메소드를 가지고 있지만 실제 실행을 시켜보니 자식 클래스에 정의되어 있는 클래스가 먼저 호출되었습니다. 이건 선언 시점의 문제이고, 당연히 나중에 선언된 클래스인 자식 클래스의 메소드가 마지막으로 기존에 생성되어 있던 부모 클래스의 메소드를 덮어씌우는 현상이 발생한 것 입니다. 이것은 오류가 아니고 지극히 당연한 현상이라고 생각하시면 됩니다.

### Hello ES7, class property in javascript

{% code-tabs %}
{% code-tabs-item title="newES7.js" %}
```javascript
class NewClass {
    helloNewProperty = '12345';
    
    constructor() {}
}

```
{% endcode-tabs-item %}
{% endcode-tabs %}

이렇게 클래스를 선언하고, node.js 런타임을 실행하게 되면 에러가 발생합니다. 지금의 문법은 ES7문법 입니다. 아직 node.js런타임에서는 받아들이지 않고 있는 자바스크립트 최신 문법 입니다. 하지만 앞서 살펴본 babel을 이용하면 저 문법을 사용해도 에러가 나지 않는 프로그래밍을 진행할 수 있습니다. 다행히도 우리가 앞으로 리액트 수업을 진행하면서 CRA라는 리액트에서 제공하는 리액트 앱 개발용 보일러플레이트를 사용하게 되는데, CRA에서는 기본적인 최신 문법을 사용할 수 있게 자동으로 설정이 되어 있습니다. 앞으로 강의를 진행 하면서 저런 형태의 class property를 많이 생성할 것 입니다. _**강의에서 생성한 클래스를 순수한 node.js런타임으로 실행시켰을 때 오류가 나도 최신 문법을 못 받아들이는구나 라고 생각하시면 됩니다.**_

