---
description: 자바스크립트의 Class문법에 관한 내용입니다. 강의 시작 전 보시면 정말 좋습니다.
---

# Class

### 자바스크립트 클래스 강의 

object {} 자료형은 간단한 텍스트나 숫자를 담을 수도 있고, 함수를 담아 사용할 수도 있습니다. 하지만 열심히 쌩코딩 하다보면 동일한 속성과 자료을 가진 object를 여러개 만들어야할 일이 생깁니다.

그럴 때 쓸 수 있는 문법이 바로 Class 문법입니다. 1. **Class** 문법을 이용해 '새로운 object 생성자' 역할을 하는 친구를 만들어놓고, 2. **new** 키워드를 이용해 생성자가 가지고 있던 **속성**과 자료를 쏙 빼닮은 object를 아주 쉽게 무한정 뽑아낼 수 있습니다. \(class를 이용하는 이유는 이것 말고도 더 있지만 지금은 이것만 설명해드릴게요\)

그럼 object 뽑아내는 '생성자'라는 것을 하나 만들어봅시다. 옛 자바스크립트 문법은 따로 생성자를 만드는 문법이 없었고 **function과 this**라는 키워드를 빌려서 생성자를 만들어내야합니다.

```javascript
function pastClass (myName) {
    this.myName = myName;
    this.pastClass = 'pastClass';
} 
let newObject = new pastClass('Lee jihoon');
console.log(newObject.myName)
```

이런 식으로 pastClass 라는 생성자를 만들어냅니다. 그 후 new pastClass\(\) 처럼 new 키워드를 이용해 새로운 오브젝트를 손쉽게 뽑아낼 수 있죠. 새로 뽑은 오브젝트인 newObject는 function 키워드 안에 들어있던 myName, pastClass 등 여러가지 속성들을 사용할 수 있습니다. \(참고로 새로 뽑은 오브젝트마다 myName 값을 다르게 설정해주고 싶다면 function 내부의 인자를 이용하면 됩니다.\)

생성자\(부모\)로부터 속성들을 물려받아 새로운 object\(자손\)를 만들어내는 이런 과정을 프로그래밍에선 **상속**이라고 표현합니다. 



잠깐 상속기능의 원리를 깊게 들여다보는 시간을 가져봅시다. 자바스크립트는 약간 특이한 방식으로 흔히말하는 **'상속'** 기능을 구현하고 있는데 **prototype** 라는 것을 이용합니다. function 이라는 키워드를 이용하는 순간 prototype이라는 속성이 pastClass 라는 생성자\(부모\)에 몰래 추가됩니다. prototype은 부모가 물려줄 속성들을 전부 담고 있는 일종의 '유전자'라고 보시면 됩니다. 

그럼 예를 들어서, 갑자기 자손들에게 전부 getInfo\(\)라는 속성을 부여하고 싶다고 가정해봅시다. 그럼 어떻게 해야할까요. 부모의 유전자를 조작해서 getInfo\(\)라는 속성을 추가하면 되겠죠? 



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

const newObject = new pastClass('Lee jihoon');
console.log(newObject.getInfo()); // 'passClass Lee jihoon made by Lee'
```
{% endcode-tabs-item %}
{% endcode-tabs %}

pastClass라는 부모의 prototype에 함수를 붙이는 방식으로 메소드\(속성\)를 추가했습니다. 그럼 자손인 newObject도 getInfo\(\)를 직접 추가한 적이 없지만 getInfo\(\) 메소드를 물려받아서 자유롭게 이용가능합니다. 

어렵게 설명하자면 자손 object가 getInfo\(\)같이 내가 직접 정의하지 않은 속성들을 사용하려고 하면 부모의 prototype을 뒤져봅니다. 그래서 부모의 prototype에 getInfo\(\)가 있을 경우 이걸 참조해서 사용하게 되는게 동작원리인데, 참고로만 알아두세요.



지금 만들어진 예제를 ES6 자바스크립트에 포함된 최신 클래스 문법을 사용해 만들어봅시다. 

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

### ES6 클래스 문법에 대해 잠깐 알아보기

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

이 부분이 바로 자바스크립트에서 새로운 클래스 문법을 사용할 때의 이점이라고 볼 수 있겠네요. 다만 조금 개념이 어렵습니다. 클래스를 상속해서 클래스를 또 만들 수 있다는 개념인데, 하나의 클래스를 만들고 이걸 상속해서 다른 클래스를 만들어 보도록 하겠습니다.

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

#### super 키워드는 부모의 생성자를 호출해서 여기에 덮어 쓰라는 뜻입니다.

자바스크립트의 문법에서, 클래스를 확장 받았을 때 _\(extendsClass는 자식 클래스가 되고, pastClass는 부모 클래스가 됩니다.\),_  **자식 클래스의 생성자에서는 반드시 부모 생성자를 호출 시켜야 합니다. 그렇지 않게 되면 오류가 발생합니다.** 그 역할을 super 키워드가 하는것이고, super 키워드에 myName 값을 넘기는데, 이건 마치 클래스를 선언할 때 생성자에 넘기는 값과 동일하게 부모 생성자의 인자로 들어가게 됩니다.



자식 클래스에서의 getInfo\(\)는 약간 다른 기능을 하고 싶은데, 이럴 땐 어떻게 코드를 짜야할까요?

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

이렇게 클래스를 선언하고, node.js 에서 실행하게 되면 에러가 발생합니다. 지금의 문법은 ES7문법 입니다. 아직 node.js런타임에서는 받아들이지 않고 있는 자바스크립트 최신 문법 입니다. 하지만 앞서 살펴본 babel을 이용하면 저 문법을 사용해도 에러가 나지 않는 프로그래밍을 진행할 수 있습니다. 다행히도 우리가 앞으로 리액트 수업을 진행하면서 CRA라는 리액트에서 제공하는 리액트 앱 개발용 보일러플레이트를 사용하게 되는데, CRA에서는 기본적인 최신 문법을 사용할 수 있게 자동으로 설정이 되어 있습니다. 앞으로 강의를 진행 하면서 저런 형태의 class property를 많이 생성할 것 입니다. _**강의에서 생성한 클래스를 순수한 node.js런타임으로 실행시켰을 때 오류가 나도 최신 문법을 못 받아들이는구나 라고 생각하시면 됩니다.**_

