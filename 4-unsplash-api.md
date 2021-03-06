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

![componentDidMount&#xB97C; &#xC774;&#xC6A9;&#xD574;&#xC11C; API&#xB97C; &#xCCAB; &#xD398;&#xC774;&#xC9C0; &#xB85C;&#xB529; &#xC2DC;&#xC5D0; &#xC694;&#xCCAD; &#xD588;&#xC2B5;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-14-10.08.37.png)

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

전부 완료한 뒤에 브라우저 화면을 보면 의도한 대로 잘 출력됩니다.

![&#xC6D0;&#xD588;&#xB358; &#xC751;&#xB2F5; &#xAC12;&#xC774; &#xC624;&#xACE0; &#xC788;&#xC2B5;&#xB2C8;&#xB2E4;. &#xB354;&#xC774;&#xC0C1; &#xBE48; &#xD654;&#xBA74;&#xC774; &#xC544;&#xB2D9;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-13-4.02.33.png)

### 더 보기 버튼을 이용해서 더 많은 사진을 불러오기

현재 웹 사이트 로딩 시 새로운 사진 데이터를 불러오는 API를 활용해서 우리가 볼 수 있도록 하고 있습니다. 그러나 더 많은 사진을 보거나 새로운 사진을 보기 위해서는 새로고침이 필요합니다. 더 많은 사진을 불러오는 기능을 추가 해 보도록 하겠습니다.

단순한 버튼 한개가 들어있는 컴포넌트를 제작해 보도록 하겠습니다. src/components폴더에 load-more.js파일을 생성해 주세요.

![load-more.js](.gitbook/assets/2019-02-14-9.12.30.png)

styled 컴포넌트 값 입니다.

{% code-tabs %}
{% code-tabs-item title="StyledComponent Values" %}
```javascript
const WrapButton = styled.div`
  display: flex;
  justify-content: center;
`;
const Button = styled.button`
  font-size: 1.5rem;
  padding: 1rem;
  margin: 1rem;
  border: 1px solid #333333;
  border-radius: 0.5rem;
  color: black;
  cursor: pointer;
`;
```
{% endcode-tabs-item %}
{% endcode-tabs %}

이 컴포넌트가 하는 역할은, 단지 버튼을 눌렀을 때에, 부모로부터 받은 loadMore이라는 props를 실행시켜 주는 일 입니다. 이제 부모 Props를 주는 App.js에 LoadMore 컴포넌트를 불러와 주어야 합니다. App.js를 다음과 같이 수정해 주세요.

![render &#xBD80;&#xBD84;&#xB9CC; &#xC218;&#xC815;&#xB418;&#xC5C8;&#xC2B5;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-14-9.55.32.png)

이후 브라우저에서 화면을 보면 다음과 같은 모습을 볼 수 있습니다.

![&#xBC84;&#xD2BC;&#xC744; &#xB204;&#xB974;&#xAC8C; &#xB418;&#xBA74; &#xC0AC;&#xC9C4;&#xC744; &#xBD88;&#xB7EC;&#xC624;&#xAC8C; &#xB429;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-14-9.21.11.png)

### 사용성 증대를 위한 로딩 효과 구현

지금까지 기능은 잘 동작하고 있네요. 그러나 한가지 문제점은, API를 호출하는 과정에서 응답을 받아 setState가 일어나기 전 까지는 API가 로딩 중인지, 혹시나 버그로 인해서 로딩이 실패했는지를 알 수가 없습니다. 사용자에 어림짐작으로 너무 로딩 시간이 길어지면 오류가 생기지 않았나 생각하게 만들죠. 이것은 사용자로 하여금 불편함을 유발하기 때문에 좋은 웹 페이지라고 할 수가 없습니다. 이것을 개선해 보도록 하겠습니다.

src/components 폴더에 loader.js, loader.scss 파일을 생성해 주세요.

![&#xB85C;&#xB529; &#xCEF4;&#xD3EC;&#xB10C;&#xD2B8; &#xC785;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-14-9.40.28.png)

이 컴포넌트는 단순히 svg파일만을 담고 있습니다. css도 로딩되는 것처럼 도와주기 위한 것 밖에는 들어있지 않습니다.

{% code-tabs %}
{% code-tabs-item title="loader.js" %}
```javascript
import React, { Component } from 'react';
import './loader.scss';

// Thank you for https://codepen.io/akwright/ Alex
class Loader extends Component {
  render() {
    return (
      <div className="modal transparent-black-background">
        <div className="modal-card loading-container">
          <svg version="1.1" id="preloader6" width="140px" height="140px" viewBox="0 0 200 200">
            <g className="pre load6">
              <path
                fill="#1B1A1C"
                d="M124.5,57L124.5,57c0,3.9-3.1,7-7,7h-36c-3.9,0-7-3.1-7-7v0c0-3.9,3.1-7,7-7h36
	C121.4,50,124.5,53.1,124.5,57z"
              />
              <path
                fill="#1B1A1C"
                d="M147.7,86.9L147.7,86.9c-2.7,2.7-7.2,2.7-9.9,0l-25.5-25.5c-2.7-2.7-2.7-7.2,0-9.9l0,0
	c2.7-2.7,7.2-2.7,9.9,0L147.7,77C150.5,79.8,150.5,84.2,147.7,86.9z"
              />
              <path
                fill="#1B1A1C"
                d="M143,74.5L143,74.5c3.9,0,7,3.1,7,7v36c0,3.9-3.1,7-7,7l0,0c-3.9,0-7-3.1-7-7v-36
	C136,77.6,139.1,74.5,143,74.5z"
              />
              <path
                fill="#1B1A1C"
                d="M148.4,112.4L148.4,112.4c2.7,2.7,2.7,7.2,0,9.9L123,147.7c-2.7,2.7-7.2,2.7-9.9,0h0c-2.7-2.7-2.7-7.2,0-9.9
	l25.5-25.5C141.3,109.6,145.7,109.6,148.4,112.4z"
              />
              <path
                fill="#1B1A1C"
                d="M125.5,143L125.5,143c0,3.9-3.1,7-7,7h-36c-3.9,0-7-3.1-7-7l0,0c0-3.9,3.1-7,7-7h36 C122.4,136,125.5,139.1,125.5,143z"
              />
              <path
                fill="#1B1A1C"
                d="M52.3,113.1L52.3,113.1c2.7-2.7,7.2-2.7,9.9,0l25.5,25.5c2.7,2.7,2.7,7.2,0,9.9h0c-2.7,2.7-7.2,2.7-9.9,0
	L52.3,123C49.5,120.2,49.5,115.8,52.3,113.1z"
              />
              <path
                fill="#1B1A1C"
                d="M57,75.5L57,75.5c3.9,0,7,3.1,7,7v36c0,3.9-3.1,7-7,7h0c-3.9,0-7-3.1-7-7v-36C50,78.6,53.1,75.5,57,75.5z"
              />
              <path
                fill="#1B1A1C"
                d="M86.9,52.3L86.9,52.3c2.7,2.7,2.7,7.2,0,9.9L61.5,87.6c-2.7,2.7-7.2,2.7-9.9,0l0,0c-2.7-2.7-2.7-7.2,0-9.9
	L77,52.3C79.8,49.5,84.2,49.5,86.9,52.3z"
              />
            </g>
          </svg>
        </div>
      </div>
    );
  }
}

export default Loader;


```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="loader.scss" %}
```css
.modal {
  position: fixed; /* Stay in place */
  z-index: 1; /* Sit on top */
  left: 0;
  top: 0;
  width: 100%; /* Full width */
  height: 100%; /* Full height */
  overflow: auto; /* Enable scroll if needed */
  background-color: hsla(0, 0%, 0%, 0.502);

  .modal-card {
    position: static;

    @media screen and (max-width: 768px) {
      width: 300px; /* Could be more or less, depending on screen size */
    }
    @media screen and (min-width: 769px) and (max-width: 1119px) {
      width: 360px;
    }
    @media screen and (min-width: 1120px) {
      width: 420px; /* Could be more or less, depending on screen size */
    }

    margin: 15% auto; /* 15% from the top and centered */
    padding: 20px;

    .modal-header {
      display: flex;
      justify-content: space-between;
    }

    .modal-footer {
      display: flex;
      justify-content: flex-end;
    }

    > div {
      margin-top: 0.5rem;
      margin-bottom: 0.5rem;
    }

    > div:nth-child(1) {
      margin-top: 0.25rem;
      margin-bottom: 1.5rem;
    }

    > div:nth-last-child(1) {
      margin-top: 2rem;
      margin-bottom: 0.25rem;
    }
  }
}

.loading-container {
  display: flex;
  justify-content: center;
}

@for $i from 1 through 8 {
  .load6 path:nth-of-type(#{$i}) {
    -webkit-animation: spin_single 1s cubic-bezier(0.215, 0.61, 0.355, 1) infinite;
    animation: spin_single 1s cubic-bezier(0.215, 0.61, 0.355, 1) infinite;
  }
}
.pre path {
  -webkit-transform-origin: 50% 50%;
  transform-origin: 50% 50%;

  -webkit-transform: translate3d(0, 0, 0);
  transform: translate3d(0, 0, 0);

  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}
@-webkit-keyframes spin_half {
  0% {
    -webkit-transform: rotate(0deg);
  }
  50% {
    -webkit-transform: rotate(360deg);
  }
}
@keyframes spin_half {
  0% {
    transform: rotate(0deg);
  }
  50% {
    transform: rotate(360deg);
  }
}
@-webkit-keyframes spin_full {
  0% {
    -webkit-transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(360deg);
  }
}
@keyframes spin_full {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
@-webkit-keyframes spin_single_neg {
  0% {
    -webkit-transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(-180deg);
  }
}
@keyframes spin_single_neg {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(-180deg);
  }
}
@-webkit-keyframes spin_single {
  0% {
    -webkit-transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(180deg);
  }
}
@keyframes spin_single {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(180deg);
  }
}

```
{% endcode-tabs-item %}
{% endcode-tabs %}

이제 이 파일들을 API 로딩이 시작했을 때와 끝나기 전 까지 보여주어야 합니다. 그 부분을 제작해 보도록 하겠습니다. App.js파일을 다음과 같이 수정해 주세요. state를 하나 추가하고, getImages 부분을 수정할 것 입니다.

![state&#xB97C; &#xCD94;&#xAC00;&#xD588;&#xC2B5;&#xB2C8;&#xB2E4;. ](.gitbook/assets/2019-02-14-9.51.50.png)

메소드 시작과 동시에 isPending이라는 state가 true로 변경되고, API호출이 끝남과 동시에 다시 isPending이라는 변수가 false로 변경됩니다. 이제 이 변수에 맞추어서 Loader 컴포넌트를 보여주면 됩니다. render부분에 Loader 컴포넌트를 불러와 주세요. 단 isPending이 true일때만 불러와야 합니다. App.js의 render부분을 사진과 같이 수정해 주세요.

![Loader &#xCEF4;&#xD3EC;&#xB10C;&#xD2B8;&#xB97C; &#xBD88;&#xB7EC;&#xC654;&#xC2B5;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-14-9.53.59.png)

isPending이라는 state가 true인 조건을 걸어, 그 조건이 활성화 되었을때만 _\(&&, and연산과 같음\)_ Loader컴포넌트가 보여지도록 했습니다.

### 에러 핸들링

만약 axios를 통한 API요청이 실패했을 때는 어떻게 처리를 해 주어야 할까요? 현재 상태에서는 에러가 나면, 이전에 걸어두었던 isPending: true인 상태가 해제 되지도 않을 뿐더러 어디에서도 에러를 처리해주는 부분이 없어서 에러가 나게 됩니다. 이 부분을 해결해 보도록 하겠습니다. App.js를 사진과 같이 수정해 주세요.

![catch&#xB97C; &#xD1B5;&#xD55C; &#xC5D0;&#xB7EC; &#xD578;&#xB4E4;&#xB9C1;](.gitbook/assets/2019-02-15-12.44.40.png)

catch는 Promise로 반환되는 값에서 모두 사용할 수 있습니다. 특정한 코드가 실행되는 도중에 에러가 발생하게 되면 catch에 작성되어 있는 함수로 넘어갑니다. 이를 통해서 axios를 통한 API요청이 실패해도 정상적으로 재 로딩을 시도할 수 있습니다.

