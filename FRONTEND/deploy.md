# Deploy
프론트엔드에서 배포란 사용자 인터페이스를 인터넷, 웹사이트에 공개하는 과정을 말한다.

HTML, CSS, JavaScript와 같은 언어로 코드를 작성하고 이 코드를 웹 서버로 전송하여 사용자가 접근할 수 있게 하는 것을 포함한다.

웹 개발에서 배포는 중요하다. 왜냐하면 아무리 개발을 열심히 잘 했어도 배포를 하지 않으면 사용자들과 내가 만든 웹과 상호 작용할 수 없기 때문이다. 

결국 웹사이트에 배포를 해야 하기 때문에 웹 개발에서 배포는 빠질 수 없는 부분이다. 또, 배포가 잘 된다면 내 웹사이트가 최적의 성능을 낼 수 있게한다.

## Flatform

### vercel
클라우드 서비스형 플랫폼 회사이자 웹 사이트의 이름이다. Next.js 프레임워크를 유지 관리하기도 한다.

vercel을 통해 배포하면 git 저장소를 통해 처리되며 github말고도 gitlab, bitbucket 저장소도 지원한다.

vercel로 배포를 하면 vercel.app 이라는 도메인 아래에 하위 도메인을 부여 받는데 배포를 위한 사용자 지정 도메인도 지원한다.

### netlify

웹 프로젝트를 만들고 배포할 때 더욱 쉽게 할 수 있도록 도와주는 사이트이다.

배포도 쉽게 하도록 도와주지만 변경 사항들도 자동으로  적용해주어 웹사이트의 유지 보수도 도와준다.
### github pages

github에서 제공하는 정적 웹사이트 호스팅 서비스이다. 자신의 저장소에서 웹페이를 구동할 수 있도록 도와준다.

주로 간단한 사이트를 만드는 데 사용된다.

## Step

### 코드 작성

당연히 배포하려면 웹 프로젝트가 필요하다. 이를 만들기 위해 HTML, CSS, JavaScript, React, Vue, Angular 등을 이용해 개발한다.

### 테스팅

내가 만든 웹 프로젝트가 내 예상대로 잘 동작하는 지 확인하는 과정이 필요하다. 테스트하는 과정에서 여러 오류들을 찾거나 추가적으로 여러 브라우저에서 잘 동작하는지도 테스트한다.

### 번들링, 빌드

테스트를 마쳤다면 여러 모듈들을 하나로 합치는 번들링을 하고 빌드를 해야한다.

이 단계에서는 내가 작성한 코드를 컴파일하고 성능을 최적화 하는 데에 더 초점이 맞춰진다. 

Minification(코드 축소)과 js parser가 해석할 수 없는 문법을 예전 문법이나 표준적인 문법으로 바꾸는 Transpiling 작업도 한다.

이 외에도 나무를 흔들면 썩은 나뭇잎이 떨어지는 것에서 유래한 Tree Shaking. 쓰이지 않는 코드를 삭제하는 것도 빌드 단계에 포함된다.

css preprocessor(sass, less), css in js (emotion, styled-components) 들은 브라우저에서 지원되지 않는 문법이라 빌드 단계에서

컴파일하는 CSS Build 등 다양한 작업들이 이루어지기 때문에 배포 전에 거쳐야 하는 단계이다.

### 배포

이 작업들을 모두 마쳤다면 배포를 할 수 있다. 여러 배포 플랫폼을 이용해 웹 프로젝트를 업로드하고 각 플랫폼에서 필요로 하는 요구 사항을 작성하고 배포한다.

배포가 완료되면 사용자들과 내 웹 사이트가 상호 작용할 수 있게 된다.


