---
description: Routing 실습 토이 프로젝트
---

# 3강 - 한국 전통 음식 소개 페이지 만들기

음식 소개 페이지를 만들어 보도록 하겠습니다. 페이지는 두 개로 구성됩니다. 첫 페이지는 한국 전통 음식 리스트, 두 번재 페이지는 특정 전통 음식의 자세한 소개 페이지 입니다. 라우팅을 통해서 매끄럽게 페이지 전환을 해 보도록 할 것입니다. 먼저 프로젝트를 한 개 생성해 주시고 [작업이 가능한 상태로 프로젝트를 비워 주세요.](https://ljh86029926.gitbook.io/codingapple-react-class/create-reactapp-using-cra-5min)

### 프로젝트 세팅하기

![](.gitbook/assets/2019-02-04-2.35.52.png)

scss, styled-components, 그리고 우리가 배운 react-router-dom도 설치해 주도록 하겠습니다.\`\`\`

{% code-tabs %}
{% code-tabs-item title="Third-party modules" %}
```text
yarn add node-sass or npm i node-sass
yarn add styled-components or npm i styled-components
yarn add react-router-dom or npm i react-router-dom
```
{% endcode-tabs-item %}
{% endcode-tabs %}

[라우팅을 준비할 때](route-prepare.md) BrowserRouter 라는 컴포넌트를 한 번 감싸 주었습니다. 이 프로젝트에도 똑같이 적용해 주시면 될 것 같습니다.

![router-wrapper.js, &#xC774;&#xC81C; index.js&#xC5D0; &#xC801;&#xC6A9;&#xC744; &#xD574; &#xC8FC;&#xACA0;&#xC2B5;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-04-3.29.06.png)

![index.js](.gitbook/assets/2019-02-04-3.29.46.png)

기본적인 세팅이 끝났습니다. 다음은 데이터 세팅입니다.

### 데이터 세팅

데이터 파일을 만들어 보겠습니다. 음식 소개 텍스트와 더불어 사진 같은 데이터를 먼저 만들어 두겠습니다. src 폴더 안에 food-data.js 파일을 생성해 주세요. 이 파일에 우리가 소개할 음식 데이터를 넣어줄 것 입니다.

![food-data.js](.gitbook/assets/2019-02-04-3.31.02.png)

데이터를 넣어 주겠습니다. 다음 코드를 그대로 foot-data.js에 복사해 주세요.

{% code-tabs %}
{% code-tabs-item title="food-data.js" %}
```javascript
const foodData = [
  {
    name: '김치',
    photo: 'https://upload.wikimedia.org/wikipedia/commons/f/f8/Various_kimchi.jpg',
    subIntro:
      '배추, 무 등을 굵은 소금에 절여 씻은 다음 고춧가루, 파, 마늘, 생강 등의 양념과 젓갈을 넣어 버무려 만드는 한국의 저장 발효식품.',
    mainIntro: `배추, 무 등을 굵은 소금에 절여 씻은 다음 고춧가루, 파, 마늘, 생강 등의 양념과 젓갈을 넣어 버무려 만드는 한국의 저장 발효식품이다. 
    김치의 종류는 많지만 일반적으로 알려진 매운 김치의 경우, 대표적인 조미료는 고춧가루와 젓갈 등이며, 한국에서는 지방마다 제조 과정이나 종류가 조금씩 다르다. 
    올림픽, 아시안 게임, FIFA 월드컵 공식 지정 식품이기도 하다.`,
    cookingMethod:
      '겨울철에 채소에다 소금, 젓갈 등을 버무리는 김장을 통해 제조되며, 전통 사회에서는 김장독을 땅에 파묻어 숙성시켰으나 현대에는 이 원리를 응용한 김치냉장고에 보관하여 숙성시킨다.',
    spec: '배추, 무, 고춧가루, 파, 마늘, 생강, 젓갈, 등...'
  },
  {
    name: '된장찌개',
    photo: 'https://upload.wikimedia.org/wikipedia/commons/thumb/a/a5/Doenjang_jjigae.jpg/440px-Doenjang_jjigae.jpg',
    subIntro: '끓는 육수에 된장을 풀고 육류나 어패류, 채소, 두부, 버섯을 비롯한 각종 재료를 넣어 끓인 찌개이다.',
    mainIntro: `끓는 육수에 된장을 풀고 육류나 어패류, 채소, 두부, 버섯을 비롯한 각종 재료를 넣어 끓인 찌개이다. 
    아욱, 미역, 시금치, 배추, 무청 얼갈이를 넣은 된장국과도 비슷하다. 
    육류와 어패류를 함께 넣는 경우는 거의 없다. 
    계절에 따라서 봄에는 풋고추, 겨울에는 시래기를 넣기도 한다. 
    한국인들이 김치찌개 만큼이나 많이 찾는 음식이다. 
    토장찌개라고도 한다. 
    한국의 각종 고기구이 전문 식당에서 고기를 먹은 후에 내놓은 식사류로 많이 이용된다.`,
    cookingMethod: `된장찌개를 만드는 과정은 개인에 따라 순서나 재료에 차이가 있지만, 대부분 아래와 비슷한 과정을 따른다. 
    먼저, 뚝배기에 물을 넣은 후 멸치와 무를 넣고 국물을 우려낸다. 
    국물이 충분히 우러나 맛국물이 만들어지면 된장을 풀고 다시 끓인다. 
    된장이 끓고 있는 동안 된장에 들어갈 재료를 썬다. 
    재료는 개인에 따라 다르지만, 일반적으로 감자, 파, 청양 고추, 애호박, 버섯, 두부가 들어간다. 
    된장국이 충분히 끓으면 미리 썰어놓은 재료를 넣고 다시 끓인다. 
    이 때, 두부는 넣지 않는데, 그 이유는 두부는 쉽게 물러지기 때문이다. 
    두부는 완성되기 직전에 넣고 찌개를 짧게 끓여준다.`,
    spec: '된장, 두부, 파,  감자, 애호박, 고추, 팽이버섯, 쇠고기, 조개, 바지락, 우렁이, 등...'
  },
  {
    name: '비빔밥',
    photo: 'https://upload.wikimedia.org/wikipedia/commons/thumb/4/44/Dolsot-bibimbap.jpg/440px-Dolsot-bibimbap.jpg',
    subIntro:
      '비빔밥 또는 교반(攪飯)은 대표적인 한국 요리의 하나로, 밥에 고기나 거섶(나물), 달걀 등과 고추장, 참기름 등 양념을 넣고 비벼서 섞어 먹는 음식이다. ',
    mainIntro: `비빔밥 또는 교반(攪飯)은 대표적인 한국 요리의 하나로, 밥에 고기나 거섶(나물), 달걀 등과 고추장, 참기름 등 양념을 넣고 비벼서 섞어 먹는 음식이다. 
    부빔밥이나 재삿밥, 골동반(骨董飯) 등으로도 부르며, 궁중에서는 비빔이라 불렀다.`,
    cookingMethod: '재료를 넣은 뒤, 비비면 왼성된다.',
    spec: '콩나물, 오이, 고사리, 당근, 버섯, 양파, 무우(생채), 도라지, 시금치 등 각종 나물 + 고추장, 쇠고기, 참기름, 볶음고추장, 등...'
  }
];

export default foodData;
```
{% endcode-tabs-item %}
{% endcode-tabs %}

이제 이 데이터를 App.js의 state로 만들어 주도록 하겠습니다. App.js의 파일을 다음과 같이 변경해 주세요.

![App.js state &#xC138;&#xD305;](.gitbook/assets/2019-02-04-3.31.55.png)

### 페이지 구성

* /foods - 전체 음식이 들어가 있는 부분입니다
* /foods/:foodName - 음식 이름에 따라서 각 음식에 대한 정보를 알려 줍니다.

### 전통음식 미리보기 컴포넌트 만들기

우리가 만들 라우트는 /foods에 대한 라우트 입니다.

미리보기 컴포넌트를 통해 카드 형태로 전통음식 리스트를 보여 줍니다. 각각의 리스트를 클릭하게 되면, 상세보기로 이동합니다. 카드 형태로 전통음식의 특징을 미리보기 할 수 있는 컴포넌트를 제작해 보도록 하겠습니다.

src폴더 내에 food-card.js 파일을 생성해 주세요.

![food-card.js](.gitbook/assets/2019-02-08-12.07.02.png)

이 카드는 대략적인 음식의 정보를 받아 음식의 이름, 간략한 소개만 보여줄 수 있는 카드 형태의 컴포넌트가 될 예정입니다. food-card.js 컴포넌트를 제작해 보도록 하겠습니다.

![&#xC804;&#xD1B5;&#xC74C;&#xC2DD; &#xCE74;&#xB4DC; &#xCEF4;&#xD3EC;&#xB10C;&#xD2B8;](.gitbook/assets/2019-02-09-4.08.34.png)

이 컴포넌트는 음식의 자세한 정보를 알기 전, 간략한 정보만을 축약해서 보여줄 수 있는 페이지입니다. 따라서 음식의 이름과, subIntro라는 간단한 소개 글만 있는 컴포넌트 입니다. scss파일도 하나 만들어서 넣어 주세요.

{% code-tabs %}
{% code-tabs-item title="food-card.scss" %}
```css
.food-card {
  display: flex;
  flex-direction: column;
  border: 1px solid #dfe7f2;
  border-radius: 0.5rem;

  .food-card-name {
    margin-top: 0.5rem;
    margin-bottom: 0.75rem;
    margin-left: 0.5rem;
    margin-right: 0.5rem;
    > span {
      font-size: 1.5rem;
      font-weight: bold;
    }
  }

  .food-card-content {
    margin-bottom: 0.75rem;
    margin-left: 0.5rem;
    margin-right: 0.5rem;
  }
}

```
{% endcode-tabs-item %}
{% endcode-tabs %}

이제 완성한 컴포넌트를 보여주는 일이 남았습니다. 그러기 위해서는 음식 데이터의 리스트를 조합해서 하나의 카드로 보여줄 수 있는 리스트 컴포넌트가 필요합니다. 

### 전통음식 미리보기 컴포넌트 리스트 만들기

src 폴더에 food-card-list.js 파일을 생성해 주세요.

![food-card-list.js](.gitbook/assets/2019-02-09-4.11.30.png)

리스트 컴포넌트를 작성해 보겠습니다.

![&#xC74C;&#xC2DD; &#xB9AC;&#xC2A4;&#xD2B8; &#xCEF4;&#xD3EC;&#xB10C;&#xD2B8; &#xC785;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-09-4.13.44.png)

리스트 컴포넌트와 카드 컴포넌트를 완성했으니, 남은 것은 App.js에 적용해주는 일이 남았습니다.

![Route](.gitbook/assets/2019-02-09-4.31.26.png)

여기에 지금까지 배웠던 예제와 다른 속성이 Route에 있는 것을 볼 수 있습니다. 바로 render 인데요, 이것을 사용한 이유는, 넘겨주는 컴포넌트인 FoodCardList 컴포넌트가 음식 리스트를 Props로 받기 때문입니다. 

#### Render를 사용하면, props를 담아서 라우팅을 할 수 있습니다.

component={컴포넌트 이름} 형태로 출력하게 되면, FoodCardList 컴포넌트가 받아야 할 음식 리스트를 받지 못하게 됩니다. render 컴포넌트는, 라우팅되는 컴포넌트에 Props를 전해주고 싶을 때 사용하는 컴포넌트 입니다. Arrow function을 사용하는 형태로 작성합니다.

추가로, App.scss도 조금 변경 되었습니다.

{% code-tabs %}
{% code-tabs-item title="App.scss" %}
```css
#app-container {
  display: flex;
  flex-direction: column;
  align-items: center;

  #app {
    max-width: 720px;

    #app-header {
      margin-top: 0.5rem;
      margin-bottom: 2rem;
      > span {
        font-size: 2rem;
        font-weight: bold;
      }
    }

    #app-food-card-container {
      .food-card:nth-last-child(1) {
        margin-bottom: 0;
      }
      .food-card {
        margin-bottom: 1rem;
      }
    }
  }
}

```
{% endcode-tabs-item %}
{% endcode-tabs %}

[http://localhost:3000/foods](http://localhost:3000/foods) 로 들어가보면, 우리가 작성한 컴포넌트가 매우 잘 동작하는 것을 확인 할 수 있습니다.

![Foods](.gitbook/assets/localhost_3000_foods-iphone-6_7_8.png)

### 전통음식 상세보기 컴포넌트 만들기

라우터를 통해 특정 음식의 정보를 알고 싶을 때 사용하는 컴포넌트 입니다. 라우트 주소는 미리 정해두었던 데로, foods/:foodName 라우트로 들어왔을 때 각 음식 이름 별로 처리를 해 주는 것으로 하겠습니다. 지금 경우에는 3개의 전통음식 상세보기 페이지가 만들어 질 예정입니다. 소개할 음식이 3가지니까, 라우트도 /foods/김치, /foods/된장찌개, /foods/비빔밥, 이렇게 3가지의 라우트에 따라서 각각의 상세 보기 페이지가 만들어 질 예정입니다. 그러나 컴포넌트는 하나만 있으면 충분합니다.

우선, food-specific 컴포넌트를 하나 만들어 주도록 하겠습니다.

![food-specific.js](.gitbook/assets/2019-02-09-4.41.31.png)

이번 컴포넌트는 제법 깁니다. 그러나 특별한 부분은 render내부에 있는 함수 한 개밖에 없습니다.

![1 ~ 47&#xC904; &#xAE4C;&#xC9C0;](.gitbook/assets/2019-02-09-5.54.04.png)

![28 ~ &#xB05D;&#xAE4C;&#xC9C0;](.gitbook/assets/2019-02-09-5.54.10.png)

render 함수 내부에 있는 renderText 함수는, 말 그대로 문자열 텍스트를 받아서, 엔터 를 기준으로 배열을 생성한 후, map 함수를 이용해서 문장 하나하나 p태그에 담아서 출력하는 부분입니다. 이 부분이 필요한 이유는, HTML에서 단순 문자열을 출력할 경우에 엔터 개행이 불가능 하기 때문입니다. 이미지를 보여주는 부분 같은 부분은 일전에 만들었던 미리보기 컴포넌트에서 대부분 가져와서 사용했습니다.

scss파일입니다.

{% code-tabs %}
{% code-tabs-item title="food-specific.scss" %}
```css
.food-specific-container {
  display: flex;
  flex-direction: column;
  margin-top: 1rem;
  border: 1px solid #dfe7f2;
  border-radius: 0.5rem;

  .food-specific-header {
    margin-top: 0.5rem;
    margin-bottom: 1.5rem;
    padding-right: 0.5rem;
    padding-left: 0.5rem;

    > div:nth-child(1) {
      margin-bottom: 0.5rem;
      > span {
        font-size: 2rem;
        font-weight: bold;
      }
    }
    > div:nth-last-child(1) {
      display: flex;
      flex-direction: column;
      > span:nth-child(1) {
        margin-bottom: 0.75rem;
        font-size: 1.5rem;
        font-weight: 600;
      }
    }
  }

  .food-specific-content {
    display: flex;
    flex-direction: column;
    margin-bottom: 1rem;
    padding-right: 0.5rem;
    padding-left: 0.5rem;

    > div:nth-child(1) {
      > span:nth-child(1) {
        font-size: 1.5rem;
        font-weight: 600;
      }
    }
  }
}

```
{% endcode-tabs-item %}
{% endcode-tabs %}



### Redirect 설정하기

//

### 클릭 라우트 지정해주기

//

