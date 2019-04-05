---
description: 영화 소개 프로젝트에 SCSS와 Styled-component를 넣어 봅니다.
---

# 영화 소개 프로젝트: SCSS, Styled-component

### 배경화면과 헤더를 꾸며 봅시다.

styled-components를 이용해 볼 것입니다. 우선 기존에 진행하고 있던 영화 프로젝트에 styled-components 모듈을 설치해 주세요.

`yarn add styled-components`

`npm install styled-components`

또한 이번에는 다른 컴포넌트에는 scss를 사용해서 진행할 것이기 때문에 node-sass도 같이 설치를 해 주도록 하겠습니다.

`yarn add node-sass`

`npm install node-sass`

설치가 완료되셨다면, 프로젝트 폴더를 열어 주세요.

### 기본적인 스타일 주입: Reset css

전체 CSS의 기본 스타일세팅을 리셋해주는 CSS를 사용하겠습니다.

{% embed url="https://meyerweb.com/eric/tools/css/reset/" %}

여기에 있는 CSS를 복사해 App.css안에 넣어 주세요.

![Reset css](../.gitbook/assets/2019-04-05-8.21.36.png)

이번 프로젝트에서 사용할 폰트도 같이 넣어주도록 하겠습니다. noto sans kr을 사용하겠습니다.

![https://fonts.google.com/?selection.family=Noto+Sans+KR&amp;query=noto](../.gitbook/assets/2019-04-05-11.55.07.png)

![App.css &#xCD5C;&#xC0C1;&#xB2E8;&#xC5D0; &#xC801;&#xC6A9;&#xC2DC;&#xD0B4;](../.gitbook/assets/2019-04-05-11.55.40.png)

![&#xC801;&#xC6A9;](../.gitbook/assets/2019-04-05-11.56.09.png)

###  Background color 설정

Reset css를 추가한 App.css에 원하는 색깔의 background를 설정해 주세요.

![&#xBC30;&#xACBD;&#xC0C9;&#xC740; &#xC6D0;&#xD558;&#xB294; &#xC0C9;&#xC73C;&#xB85C; &#xD558;&#xC154;&#xB3C4; &#xB429;&#xB2C8;&#xB2E4;.](../.gitbook/assets/2019-04-05-8.22.04.png)

![&#xBC30;&#xACBD;&#xD654;&#xBA74;&#xC774; &#xB9CC;&#xB4E4;&#xC5B4; &#xC84C;&#xB124;&#xC694;.](../.gitbook/assets/2019-04-05-11.51.52.png)

### Header 컴포넌트를 꾸며봅시다.

일전에 스타일 없이 작성해둔 Header 컴포넌트에 스타일을 주입해 보도록 하겠습니다. 이 부분은 스타일 작성을 많이 할 필요가 없는 부분이기 때문에, styled-components를 이용해서 간단하게 작업을 진행해 보도록 하겠습니다. 

![styled-components&#xB294; sass&#xC758; &#xBB38;&#xBC95;&#xB3C4; &#xC9C0;&#xC6D0;&#xD574; &#xC90D;&#xB2C8;&#xB2E4;.](../.gitbook/assets/2019-04-05-12.02.47.png)

_지금 현재 제가 사용하고 있는 에디터는 VScode인데요, 백틱 문자열에 담긴 CSS코드를 하이라이팅 시키기 위해서_ [_특정_ ](https://marketplace.visualstudio.com/items?itemName=jpoissonnier.vscode-styled-components)_모듈을 사용하고 있습니다._

스타일링이 끝나고 나면 제 경우에는 검은색 화면에 'Movie App' 글자가 하나 떠 있는 화면을 보실 수 있습니다.

![](../.gitbook/assets/2019-04-05-12.06.29.png)

