---
description: NodeJS의 문법 확장
---

# 개념 정립 - Babel? - 작성 중

일반 자바스크립트 문법과 create-react-app에서 작동하는 문법은 조금 많이 다릅니다. 일단 모듈을 import하는 방식부터 다른데요. 한번 비교해 볼까요 ?

```text
import react from 'react'; // create-react-app에서 사용되는 문법
const react = require('react'); // node.js에서 현재 사용되는 import 문법
```

이 문법들 간의 차이가 분명히 보이실 겁니다. 첫번째 줄과 같은 코드는 nodejs상으로는 돌아가지 않습니다. 두번째 줄과 첫번째 줄의 기능상 차이는 없습니다.

### 그런데 나는 어떻게 실행을 시켰지?

nodejs에서는 import 문법 사용이 불가능 합니다. commonJS명세서에는 import 구문이 존재하지 않기 때문이죠. 그런데 더 신기한건 리액트 개발을 CRA로 하신 분들이라면 이해가 되지 않을 수도 있습니다. 내가 작성한 문법이 실은 nodejs상 동작하지 않는 코드였다니요. 리액트 개발 보일러플레이트인 CRA에서 이렇게 컴파일이 잘되는 이유는 **Babel** 덕분입니다.

### 문법을 통일해 주는 Babel

nodejs프로그램을 실행시키기 전에, 프로덕션 빌드 파일

