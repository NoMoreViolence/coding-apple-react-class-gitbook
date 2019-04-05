---
description: for -> forEach -> map !
---

# Map

### for 문 말고 map 쓰세요 !

같은 기능을 하는 예제 두개를 만들어 볼 것입니다. 하나는 우리가 옛날부터 사용하고 있는 문법인 for문을 사용할 것이고, 또 다른 하나는 map이라는 새로운 method를 사용해서 진행해 보도록 하겠습니다. 우선 for문을 사용했을 때를 보시죠.

{% code-tabs %}
{% code-tabs-item title="for.js" %}
```javascript
const a = [1, 3, 5, 7, 9]

for (let i = 0; i < a.length; i++) {
    console.log(a[i])
}

// 1
// 3
// 5
// 7
// 9
```
{% endcode-tabs-item %}
{% endcode-tabs %}

일반적인 for문을 사용해서 배열에 있는 요소의 값을 출력해 주는 예제입니다.

다음은 map으로 구현한 예제입니다.

{% code-tabs %}
{% code-tabs-item title="map.js" %}
```javascript
const a = [1, 3, 5, 7, 9];

const aLoop = a.map((unit, idx) => {
    console.log(unit);
    return unit;
});

// 1
// 3
// 5
// 7
// 9

```
{% endcode-tabs-item %}
{% endcode-tabs %}

서로 같은 동작을 하는 코드입니다. 하지만 map쪽이 훨씬 알아보기 쉽고 더 좋은 장점을 많이 가지고 있습니다. 만약 a에 있는 배열의 내용을 변경시켜 저장하고 싶다면, map을 사용하면 훨씬 편리하게 사용이 가능합니다. map은 그 자체로 새로운 배열을 만들어 내는 메소드 이기 때문입니다. 이게 무슨 말이냐면, aLoop에 들어있는 값은 새로운 배열이라는 것 입니다. 또한 다르게 저장을 할 수도 있습니다.

{% code-tabs %}
{% code-tabs-item title="why-map.js" %}
```javascript
const a = [1, 3, 5, 7, 9];

const aLoop = a.map((unit, idx) => {
    console.log(unit);
    return unit + 1;
});

// 1
// 3
// 5
// 7
// 9

// aLoop: [2, 4, 6, 8, 10]

```
{% endcode-tabs-item %}
{% endcode-tabs %}

map의 메소드에서 원래 unit에 +1을 리턴만 해 주었는데도 새로운 배열이 생성되었습니다. 지금의 작업은 a 데이터에게는 영향을 끼치지 않으면서 새로운 배열을 만들어 낸 것입니다.

만약 우리가 예전 문법을 사용하고 있었다면, 다음과 같이 변경해야 합니다.

{% code-tabs %}
{% code-tabs-item title="for.js" %}
```javascript
const a = [1, 3, 5, 7, 9];

const newArray = [];

for (let i = 0; i < a.length; i++) {
    console.log(a[i]);
    newArray.push(a[i] + 1);
}

// 1
// 3
// 5
// 7
// 9

// newArray: [2, 4, 6, 8, 10]

```
{% endcode-tabs-item %}
{% endcode-tabs %}

Map 메소드의 좋은 점은, 배열 변수 하나만 가지고 있어도 바로 실행이 가능하다는 점 입니다. 또한 현재 값은 손상을 시키지 않기 때문에 a배열의 원래 값은 유지하면서 새로운 배열을 만들어 내는 것이 가능합니다.

### Map의 문법

```text
// 배열.map(함수를 담습니다.) // 새로운 값을 가공할 함수 또는 로직

// 배열의 요소만큼 map에 작성된 함수가 수행됩니다. 인자는 두개를 받습니다.

// 1. 현재 요소의 값, 2. 현재 배열의 크기

// example
const a = [1, 2, 3, 4, 5];

const unit = a.map( (unit, idx) => {
    return unit - 1;
} )
// unit: [0, 1, 2, 3, 4] 
console.log(unit);
```

