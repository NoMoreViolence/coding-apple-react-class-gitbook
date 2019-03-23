---
description: '자바스크립트의 import, export 개념을 탄탄히 다지고 싶으신 분들께'
---

# import, export에 관해서

모듈을 어떻게 import하고 export하는지 알려드리도록 하겠습니다.

우선 예전 자바스크립트 에서는 import와 export를 다음과 같이 표현 했었습니다.

{% code-tabs %}
{% code-tabs-item title="old-import.js" %}
```javascript
// ES5
const react = require('react');
// ES6
import react from 'react';

// 둘이 하는 일은 정확히 같습니다. 다만 밑 코드가 최신 문법 코드입니다.
// 일반적인 node.js에서는 ES5방식의 import만 지원하며, 이를 nodejs에서 원활하게
// 돌아가게 하기 위해서는 babel의 도움이 필요합니다.
```
{% endcode-tabs-item %}
{% endcode-tabs %}

require라는 키워드는 모듈을 불러오는 키워드 입니다. **그런데 한가지 궁금한 것은 이 모듈을 도대체 어디서 불러오는 걸까요?** './'와 같은 경로 지정도 하지 않았는데 말이죠. _\(그 해답은_ [_여_](node.js-npm.md#npm-scripts)_를 읽으신 후 지금 글을 읽으시면 더 잘 이해할 수 있습니다.\)_

### 경로 지정을 하지 않았을 때에는 node\_modules

모듈을 설치했을 때의 저장소가 node\_modules로 향한다는 사실은 알고 계셨나요? 모든 모듈은 설치하게 되면 node\_modules에 모듈의 파일이 저장되게 됩니다.

**node\_modules에 설치된 모듈을 불러올 때에는, 경로를 지정할 필요 없이 모듈 이름만 작성하면 됩니다.**

그렇기 때문에 우리는 리액트 모듈을 설치했을 때 따로 경로 지정을 해 두지 않아도 바로 리액트 모듈을 불러올 수 있습니다.

### import보다 많이 복잡한 export

import의 문법은 저게 다 입니다. 그저 형식만 바뀌었을 뿐 하는 일은 같습니다. 이건 export에도 동일하게 적용되는데, 헷갈릴 수 있는 부분이 존재합니다.

export의 방식 차이

{% code-tabs %}
{% code-tabs-item title="export.js" %}
```javascript
// ES5
module.exports = { hello: '12345' }


// ES6
const hello = '12345';
export { hello };
export default hello;

```
{% endcode-tabs-item %}

{% code-tabs-item title="import.js" %}
```javascript
// ES5 import
const hello = require('./export').hello; // '12345'
const theDefault = require('./export'); // { hello: '12345' }

// ES6 import
import { hello } from './export'; // '12345'
import theDefault from './export'; // '12345'

```
{% endcode-tabs-item %}
{% endcode-tabs %}

둘의 하는 일은 같습니다. 다만 눈으로 보기에도 ES6코드가 빨리 읽히고 편하다는 점에서 다들 사용하고 있습니다. 여기서 default export와 일반적인 export의 차이를 알아야 합니다. default로 export를 진행하는 경우에는, import를 할 때에 아무 이름이나 사용해서 import를 하더라도, 같은 데이터를 전송해 줍니다.



