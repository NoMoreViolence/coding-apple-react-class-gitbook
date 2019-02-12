---
description: Unsplash API를 이용한 토이프로젝트
---

# 4강 - Unsplash API를 이용한 사진첩 만들기

Unsplash API를 이용해서 간단한 사진접 프로젝트를 제작해 보도록 하겠습니다. [Unsplash](https://unsplash.com/) 는 다양한 주제의 사진을 이용할 수 있는 웹 사이트 입니다.

### Unsplash 회원가입

![https://unsplash.com](.gitbook/assets/2019-02-13-2.43.43.png)

회원이신 분들은 로그인 해 주세요. 회원이 아니신 분들은 회원 가입을 부탁 드립니다.

![&#xD68C;&#xC6D0;&#xAC00;&#xC785;&#xC740; &#xD398;&#xC774;&#xC2A4;&#xBD81;&#xC744; &#xC774;&#xC6A9;&#xD558;&#xC154;&#xB3C4; &#xAC00;&#xB2A5;&#xD569;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-13-2.45.50.png)

### Unsplash API 발급받기

API를 사용하기 위해서는 API를 사용할 수 있는 key를 발급 받아야 합니다. Developers 전용 메뉴가 있기 때문에 우선 이동해 주세요. [이동하기](https://unsplash.com/developers)

![https://unsplash.com/developers](.gitbook/assets/2019-02-13-2.48.16.png)

Your apps라는 메뉴를 누르고 들어가 주세요. 그렇게 되면 다음과 같은 화면이 나타날 것 입니다.

![&#xD604;&#xC7AC;&#xB294; &#xC571;&#xC744; &#xC544;&#xBB34;&#xAC83;&#xB3C4; &#xB9CC;&#xB4E4;&#xC9C0; &#xC54A;&#xC558;&#xAE30; &#xB54C;&#xBB38;&#xC5D0; &#xC0AC;&#xC6A9;&#xD560; &#xC218; &#xC5C6;&#xC2B5;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-13-2.49.14.png)

New Application버튼을 클릭해 Demo버전의 Application하나를 생성해 주도록 하겠습니다.

![&#xC8FC;&#xC758; &#xC0AC;&#xD56D;&#xC5D0; &#xBAA8;&#xB450; &#xCCB4;&#xD06C;&#xB97C; &#xD558;&#xACE0; &#xB2E4;&#xC74C;&#xC73C;&#xB85C; &#xB118;&#xC5B4;&#xAC11;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-13-2.51.17.png)

![&#xC5B4;&#xD50C;&#xB9AC;&#xCF00;&#xC774;&#xC158;&#xC758; &#xAE30;&#xBCF8;&#xC801;&#xC778; &#xC815;&#xBCF4;&#xB97C; &#xAE30;&#xC785;&#xD574; &#xC90D;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-13-2.52.03.png)

Create Application 버튼을 클릭하게 되면 Demo버전의 Application이 생성될 것 입니다.

![&#xC0DD;&#xC131;&#xB418;&#xC5C8;&#xC2B5;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-13-2.52.37.png)

밑으로 스크롤을 조금 해 보면 Key와 관련된 부분이 보일 것 입니다.

![&#xC808;&#xB300;&#xB85C; &#xD0A4;&#xB97C; &#xC54C;&#xB824;&#xC8FC;&#xC9C0; &#xB9C8;&#xC138;&#xC694;..!](.gitbook/assets/2019-02-13-2.55.38.png)

우리에게 필요한 키는 AccessKey 뿐입니다. 바로 가져다 사용할 수 있는 곳이나 편한 공간에 저장해 주세요.

### 프로젝트 세팅하기

이제 프로젝트를 시작할 준비가 끝났습니다. 리액트 작업에 들어가 보도록 하겠습니다.

`npx create-react-app unsplash` 를 통해 프로젝트를 하나 생성해 주시고,

`yarn add axios node-sass styled-components` or `npm i axios node-sass styled-components`설치하신 패키지 매니저에 맞추어 모듈 설치를 진행해 주세요. axios 라이브러리를 사용하는 이유는 Promise기반이기 때문에 에러 핸들링을 하기에 간편하고,  누구나 빠르게 익힐수 있을 정도로 라이브러리의 복잡도가 낮기 때문에 사용합니다.

![&#xC2DC;&#xC791;&#xD574; &#xBCF4;&#xB3C4;&#xB85D; &#xD558;&#xACA0;&#xC2B5;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-13-3.03.39.png)

![&#xD504;&#xB85C;&#xC81D;&#xD2B8;&#xC5D0; &#xC0AC;&#xC6A9;&#xD560; &#xD30C;&#xC77C;&#xC744; &#xBA3C;&#xC800; &#xC81C;&#xC791; &#xD558;&#xACA0;&#xC2B5;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-13-3.06.07.png)

![picture-list, picture&#xCEF4;&#xD3EC;&#xB10C;&#xD2B8;&#xC640; scss &#xD30C;&#xC77C;&#xC774; &#xCD94;&#xAC00; &#xB418;&#xC5C8;&#xC2B5;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-13-3.06.47.png)

기존 App.css, index.css도 확장자를 변경해 주었습니다. _logo, serviceWorker같은 파일은 지우셔도 되고 안 지우셔도 됩니다._

### State형태, 메소드 제작하기

모든 값은 App.js에서 핸들링 될 예정입니다. 당연하게도 State가 App.js에 있으니 모든 변경도 App.js에서 일어납니다.

#### State 세팅

기본적으로 어떤 데이터를 가지고 있어야 하는지를 알아야 합니다. 우선 당연히 이미지들의 URL이 string 배열 형태로 담겨져 있는 state 객체 하나면 충분합니다. 에러 핸들링을 위해서 나중에 변수 몇 개가 추가될 예정이지만, 일단 지금은 state안에 배열 하나를 생성하는 것으로 하겠습니다. App.js를 변경해 주세요.

![App.js&#xC5D0; state&#xB97C; &#xCD94;&#xAC00;&#xD55C; &#xBAA8;&#xC2B5;](.gitbook/assets/2019-02-13-3.21.21.png)

이제, 이미지를 불러오는 API를 제작 할 것 입니다. App.js에 메소드를 하나 만들어 주겠습니다.

![&#xC774;&#xBBF8;&#xC9C0;&#xB97C; &#xCD94;&#xAC00;&#xD558;&#xB294; API &#xC785;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-13-3.27.23.png)

저 메소드는 딱히 특별한 점이 없습니다. 다만 조금 이상하게 느껴질 부분이 setState부분인데요, 첫 번째 인자는 이미지를 이어준다고 치고, 두 번째 인자는 굉장히 이상한 코드같이 보입니다. 하지만 저 부분은 Unsplash의 API response값 중에서, 이미지만 빼내오려고 했기 때문에 저런 구문이 쓰여졌습니다.

![&#xD558;&#xB098;&#xC758; &#xD070; &#xBC30;&#xC5F4; &#xAC1D;&#xCCB4;&#xAC00; Response&#xB85C; &#xC751;&#xB2F5;&#xB429;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-13-3.34.29.png)

지금 사진에 보이는 count === 30이기 때문에, 랜덤 사진 요청을 보내면 30개의 랜덤 사진 요청응답이 옵니다. 그 30개의 정보들 중에서 우리에게 필요한 사이즈의 이미지 URL만 골라서 state를 업데이트 해야 하기 때문에 response를 setState하는 과정이 이상하게 느껴질 수도 있으나 필요한 부분입니다.

### 사진 컴포넌트 제작하기

사진 하나를 나타내 줄 수 있는 picture 컴포넌트를 제작해 보도록 하겠습니다.

![&#xBCC4;&#xB85C; &#xD2B9;&#xBCC4;&#xD560; &#xAC83; &#xC5C6;&#xB294; &#xCEF4;&#xD3EC;&#xB10C;&#xD2B8; &#xC785;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-13-3.55.11.png)

### 사진 리스트 컴포넌트 제작하기

picture, picture-list 컴포넌트 두 개를 만들었습니다. 그 중에 사진들의 전체적인 리스트를 관리하는 picture-list 컴포넌트를 만들어 보도록 하겠습니다.

![&#xADF8;&#xC800; &#xC774;&#xBBF8;&#xC9C0;&#xB97C; &#xBC1B;&#xC544;&#xC11C; Picture &#xCEF4;&#xD3EC;&#xB10C;&#xD2B8;&#xC5D0;&#xAC8C; &#xC804;&#xB2EC;&#xD574; &#xC8FC;&#xB294; &#xC5ED;&#xD560;&#xB9CC; &#xD569;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-13-3.56.05.png)

picture-list styled-components 부분

{% code-tabs %}
{% code-tabs-item title="picture-list.js \\" %}
```javascript
const Content = styled.div`
  margin-top: 1rem;
  /* Prevent vertical gaps */
  line-height: 0;
  @media screen and (max-width: 832px) {
    -webkit-column-count: 1;
    -webkit-column-gap: 0px;
    -moz-column-count: 1;
    -moz-column-gap: 0px;
    column-count: 1;
    column-gap: 0px;
  }
  @media screen and (min-width: 833px) and (max-width: 1232px) {
    -webkit-column-count: 2;
    -webkit-column-gap: 0px;
    -moz-column-count: 2;
    -moz-column-gap: 0px;
    column-count: 2;
    column-gap: 0px;
  }
  @media screen and (min-width: 1233px) and (max-width: 1632px) {
    -webkit-column-count: 3;
    -webkit-column-gap: 0px;
    -moz-column-count: 3;
    -moz-column-gap: 0px;
    column-count: 3;
    column-gap: 0px;
  }
  @media screen and (min-width: 1633px) {
    -webkit-column-count: 4;
    -webkit-column-gap: 0px;
    -moz-column-count: 4;
    -moz-column-gap: 0px;
    column-count: 4;
    column-gap: 0px;
  }
`;

```
{% endcode-tabs-item %}
{% endcode-tabs %}

### App.js에 적용시키기

일단 첫 번째로 해야할 일은, PictureList 컴포넌트를 App.js에 넣어주는 겁니다. props로는 images를 넣어주면 됩니다. 그 다음으로 해야할 일은 기본 API 요청 입니다. 현재 사이트에 접속했을 때에는 빈 배열이기 때문에 접속했을 때 빈 화면이 보입니다. 사진이 보이게 하기 위해서는 API요청이 가야 합니다. 적당한 LifeCycle은 componentDidMount가 있겠네요. 

![        componentDidMount&#xB97C; &#xC774;&#xC6A9;&#xD574;&#xC11C; API&#xB97C; &#xCCAB; &#xD398;&#xC774;&#xC9C0; &#xB85C;&#xB529; &#xC2DC;&#xC5D0; &#xC694;&#xCCAD; &#xD588;&#xC2B5;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-13-4.05.12.png)

{% code-tabs %}
{% code-tabs-item title="App.scss" %}
```css
.App {
  > span {
    font-size: 2rem;
    font-weight: bold;
    margin: 1rem;
  }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

전부 완료된 뒤에 브라우저 화면을 보면 의도한 대로 잘 출력됩니다.

![&#xC6D0;&#xD588;&#xB358; &#xC751;&#xB2F5; &#xAC12;&#xC774; &#xC624;&#xACE0; &#xC788;&#xC2B5;&#xB2C8;&#xB2E4;. &#xB354;&#xC774;&#xC0C1; &#xBE48; &#xD654;&#xBA74;&#xC774; &#xC544;&#xB2D9;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-13-4.02.33.png)

