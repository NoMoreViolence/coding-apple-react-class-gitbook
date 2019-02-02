---
description: 기본적인 라우팅에 관한 실습 2
---

# 3강 - Routing \(실전\)

### 기본 라우팅 실습 목표

우리는 3개의 컴포넌트를 만들어, URL에 따른 라우트 3개를 생성해 3개의 페이지를 보여주는 실습을 하도록 하겠습니다. 기본 루트 URL ' / '로 접속하는 사용자들을 위한 홈, 다음은 ' /first ', ' /second ' 의 라우트를 만들어 각각의 페이지에서 다른 페이지를 보여주는 것을 실습해 보도록 하겠습니다.

우선, src 폴더에 파일을 세 개 만들어 주도록 하겠습니다. 각각의 이름은 home.js, first.js, second.js 파일입니다. 저는 src 폴더에 components 라는 폴더를 만든 후에 이 세개의 파일들을 만들어 주도록 하겠습니다.

![&#xD3F4;&#xB354;&#xB97C; &#xD558;&#xB098; &#xB9CC;&#xB4E4;&#xC5B4; &#xB450;&#xC5C8;&#xC2B5;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-02-1.04.27.png)

![home.js, first.js, second.js &#xD30C;&#xC77C;&#xC744; &#xB9CC;&#xB4E4;&#xC5B4; &#xB450;&#xC5C8;&#xC2B5;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-02-1.04.43.png)

이제 특정 URL에 따라서, 다르게 보여지는 페이지를 만들어 보도록 하겠습니다.

3개의 컴포넌트를 일단 만들어 볼까요? 그저 각각의 컴포넌트가 어떤 컴포넌트 인지 우리가 인지할 수 있을 정도로만 만들어 주겠습니다.

![home &#xCEF4;&#xD3EC;&#xB10C;&#xD2B8;, &#xD14D;&#xC2A4;&#xD2B8;&#xB85C; home &#xCEF4;&#xD3EC;&#xB10C;&#xD2B8;&#xC784;&#xC744; &#xB098;&#xD0C0;&#xB0B4;&#xAC8C; &#xD574; &#xC8FC;&#xC5C8;&#xC2B5;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-02-1.08.06.png)

나머지 컴포넌트들도 home.js 컴포넌트와 마찬가지로, render 부분에 있는 JSX 텍스트만 바꾸어 주면서 만들어 주세요.

### URL에 따라서 다르게 보이는 페이지

이렇게 다 만들고 나면, 이제 특정 URL에 따라서 다르게 보이는 페이지를 만들어 보겠습니다. 3개의 컴포넌트를 만들기만 했으니, 이제 연결을 해 주어야겠죠? App.js 컴포넌트에 들어가 보겠습니다. 방금 전 준비 할 때 우리가 작성했었던 [App.js 컴포넌트를](3.md#browerrouter-csr), 밑에 사진과 같이 변경해 주세요.

![](.gitbook/assets/2019-02-02-1.57.12.png)

Route 태그가 바로 특정 case를 작성하는 부분 입니다. path 라는 Attribute는 URL 경로를 넣어주는 부분 입니다. _\(string 형태로 작성 합니다.\)_ component는 그 URL경로에 보여줄 컴포넌트를 넣어주는 부분 입니다. _\(객체를 넣는 스타일로 작성\)_  현재는 세 개의 컴포넌트 이름대로 path와 컴포넌트를 연결해 주었습니다. 우리는 localhost:3000 포트로 실습을 하고 있기 때문에, 'http://localhost:3000/home' 경로로 접속하게 되면 home 컴포넌트가 보이게 됩니다. 한 번 들어가 볼까요? [http://localhost:3000/home](http://localhost:3000/home) 

![home &#xCEF4;&#xD3EC;&#xB10C;&#xD2B8;&#xAC00; &#xBCF4;&#xC5EC;&#xC9C0;&#xAC8C; &#xB429;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-02-1.58.28.png)

옆에 보이는 리액트 개발자 도구는 다른 path 경로의 Route 태그는 보이지 않고 현재 경로에 맞는 태그만 보이게 됩니다. 한번 다른 경로로도 접속해 보세요. [http://localhost:3000/first](http://localhost:3000/first)

![first &#xCEF4;&#xD3EC;&#xB10C;&#xD2B8;&#xAC00; &#xBCF4;&#xC5EC;&#xC9C0;&#xAC8C; &#xB429;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-02-1.59.04.png)

### Route 컴포넌트를 사용할 때 주의할 점..!

Route 컴포넌트의 path 경로에 따라서 지정해둔 component가 보여지는 기능에 대한 것에 대한 것을 알았습니다. 이번에는 Route 태그의 맹점에 관해서 파악하고, 이를 방지하는 방법에 대해서 알아보겠습니다. 우선 이를 위해선 컴포넌트 하나를 더 만들어야 합니다. components 폴더에 main.js라는 파일을 한개 만들어 주세요.

![main.js &#xCEF4;&#xD3EC;&#xB10C;&#xD2B8;](.gitbook/assets/2019-02-02-1.51.07.png)

방금 만들었던 Main.js 컴포넌트를 App.js 부분에 적용 시켜보도록 하겠습니다.

![path=&quot;/&quot;&#xB85C; &#xB123;&#xC5B4; &#xC8FC;&#xC5C8;&#xC2B5;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-02-2.05.56.png)

path="/" 제가 이렇게 path를 넣은 이유는, 이 main 컴포넌트는 localhost:3000에서만 보여야 하고, localhost:3000/first, localhost:3000/home에서는 보이지 않아야 하는 것을 의도했기 때문입니다.   
하지만 우리가 localhost:3000/home 컴포넌트에 들어가면, 신기한 현상을 볼 수 있습니다.

![/home&#xC5D0;&#xC11C;, / path&#xB3C4; &#xAC19;&#xC774; &#xBCF4;&#xC774;&#xAC8C; &#xB418;&#xB124;&#xC694;.](.gitbook/assets/2019-02-02-2.29.12.png)

이런 현상이 나타나는 이유는, /home 라우트에는 이미 '/' 존재하고 있기 때문입니다. 이런식으로 라우트를 나열하게 되면, 중복되는 부분은 전부 보여지게 됩니다.

###  Route 컴포넌트의 의도치 않은 동작 방지 방법 1 - exact

방금과 같은 현상을 의도 했다면 상관이 없지만, 대부분은 의도하지 않았을 것 입니다. 지금 소개할 exact를 사용하게 된다면, 정확히 URL이 매치 되었을 때에만 Route 태그를 보여줄 수 있습니다.

App.js의 main 컴포넌트를 보여주는 Route 태그를 수정해 주세요.

![&#xAC04;&#xB2E8;&#xD569;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-02-2.34.04.png)

이 Attribute는, URL이 정확히 매치 되었을 때에만 Route에 있는 컴포넌트를 보여줄 수 있도록 하는 속성 중 하나 입니다. 이 태그에 JSX 스타일로,  `exact={true}` 라던지, `exact={false}` 와 같은 스타일로 작성해서, 언제든지 exact의 활성화 여부를 변경할 수 있습니다. exact만 단순히 넣어준 경우에는 기본 값 true로 취급 됩니다. 이제 [localhost:3000/home](http://localhost:3000/home)에 들어가게 되면, 우리가 의도했었던 home 컴포넌트만 보여지게 됩니다.

![exact&#xAC00; &#xC801;&#xC6A9;&#xB418;&#xC5C8;&#xC2B5;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-02-2.38.48.png)

마찬가지로, [localhost:3000](http://localhost:3000)에 들어가게 되면, 메인 컴포넌트 한개만 보이게 됩니다.

![&#xC758;&#xB3C4;&#xD55C; &#xB300;&#xB85C; &#xC798; &#xB418;&#xC5C8;&#xC2B5;&#xB2C8;&#xB2E4;.](.gitbook/assets/2019-02-02-2.39.56.png)

### Route 컴포넌트의 의도치 않은 동작 방지 방법 2 - Switch

switch는 우리가 지금 CSR을 위해 사용 중인 react-router-dom 모듈에서 제공해 주는 태그 중 하나 입니다. Route 태그 처럼 JSX 태그로 사용되며, 이 Switch 태그 안에다가 Route 컴포넌트를 넣어두면, 마치 Switch case처럼 컴포넌트들을 비교하면서 맞는 컴포넌트가 있으면 그 컴포넌트 하나만 렌더링 해 줍니다.   
App.js를 Switch를 이용해서 한 번 수정해 볼까요?

![Switch](.gitbook/assets/2019-02-02-2.44.28.png)

이제 URL이 바뀔 때 마다, Switch 태그에 걸리는 path가 있다면 그 컴포넌트만 보여 주게 되고 밑에 있는 다른 path들은 비교하지 않게 됩니다. 실제로 자바스크립트에서 사용되는 Switch case의 동작 방식과도 같아요. 단지 지금 Switch 태그들은 break가 자동으로 적용 되어있다는 점 입니다. 위 App.js 부분에서, main컴포넌트의 Route 태그를 가장 밑으로 넣어 놓았는데, 그 이유는 다음과 같습니다.

* /home, /first, /second 태그 모두 '/' 포함하고 있습니다.
* '/' 부분을 가장 앞에 놓게 되면, 어떤 URL로 들어가던지간에 main 컴포넌트만 보여지게 됩니다.

이런 이유 때문에 main 컴포넌트를 보여주는 라우트를 가장 밑으로 위치 시켰습니다. 앞으로 Switch를 사용하실 때 다들 이렇게 사용하시면 됩니다. 가장 Depth가 깊은 path를 가지고 있는 Route를 가장 먼저 Switch 앞에 위치 시키고, 그 다음 복잡한 path를 가진 Route를 나열하는 방식으로 프로그래밍 하시면 됩니다.

