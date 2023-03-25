# CSR과 SSR의 차이

# CSR
* Client Side Rendering의 약자
> 렌더링이 클라이언트 쪽에서 일어나는 것을 말한다.  
> 서버는 요청을 받으면 클라이언트에 HTML과 JS를 보내주고  
> 클라이언트는 그것을 받아 렌더링을 시작한다.  

## CSR의 순서
1. User가 Website에 요청을 보낸다.

2. CDN이 HTML파일과 JS로 접근할 수 있는 링크를 클라이언트로 보낸다.
> CDN은 AWS의 cloudFlare를 생각하면 된다. 엔드 유저의 요청에 물리적으로 가까운  
> 서버에서 요청에 응답하는 방식을 말한다.
 
3. 클라이언트는 HTML과 JS를 다운로드 받는다.
> SSR과 달리 User는 아무것도 볼 수 없다.

4. 생략

5. 다운로드가 완료된 JS가 실행된다. 데이터를 위한 API가 호출된다.
> User들은 placeholder를 보게된다.
> 
6. 서버가 API로부터 온 요청에 응답한다.
 
7. API로부터 받아온 data를 placeholder자리에 넣어준다. 이때부터 페이지는 상효작용이 가능해진다.

# SSR
* Server Side Rendering의 약자
> 서버쪽에서 렌더링 준비를 끝마친 상태로 클라이언트에 전달하는 것을 말한다.

## SSR의 순서
1. User가 Website에 요청을 보낸다.

2. Server는 'Ready to Render', 말그대로 즉시 렌더링 가능한 html파일을 만든다.
> 리소스 체크, 컴파일 후 완성된 HTML 컨텐츠로 만든다.

3. 클라이언트에 전달되는 순간, 이미 렌더링 준비가 되어있기 때문에 HTML은 즉시 렌더링 된다.
> 단, Javascript가 읽히기 전이기 때문에 사이트 자체는 조작이 불가능하다.

4. 클라이언트가 자바스크립트를 다운받는다.

5. 다운 받아지고 있는 사이에 유저는 컨텐츠는 볼 수 있지만 사이트를 조작 할 수 없다.  
> 하지만 이때 사용자 조작을 기억하고 있는다.

6. 브라우저가 JavaScript 프레임워크를 실행한다.

7. JS까지 성공적으로 컴파일 되었기 때문에 기억하고 있던 사용자 조작이 실행되고 이때부터  
   웹 페이지는 상호작용이 가능해진다.

# 차이
### 1. 웹페이지를 로딩하는 시간
> 먼저 웹페이지의 로딩은 두가지로 나뉜다. 하나는 가장 첫 페이지를 로딩하는것이고  
> 다른 하나는 나머지를 로딩하는 것이다.  
> CSR은 HTML, CSS, 모든 스크립트들을 한 번에 불러오지만 SSR은 필요한 부분의  
> HTML과 스크립트만 불러오기 때문에 첫 페이지 로딩시간은 SSR이 더 빠르다고 할 수 있다.  
> 그러나 CSR은 첫 페이지를 로딩할 때 남은 부분을 구성하는 코드를 구성하는 코드를 받고  
> SSR은 첫 페이지 로딩과정을 다시 시작하기 때문에 나머지 로딩시간은 CSR이 SSR보다 더 빠르다고 할 수 있다.

### 2. SEO 대응
> 검색엔진은 자동화된 로봇 '크롤러'로 웹 사이트들을 읽는다. CSR은 JS를 실행시켜 동적으로  
> 콘텐츠가 생성되기 때문에 자바스크립트가 실행되어야 metadata가 바뀌었는데 SSR은 애초에 서버 사이드에서  
> 컴파일되어 클라이언트로 넘어오기 때문에 크롤러에 대응하기 좋다.

### 3. 서버 자원 사용
> 이름에서부터 유추할 수 있는데 SSR이 서버 자원을 더 많이 사용한다. 매번 서버에 요청을하기 때문인데  
> 리액트로 구현할 때는 아래와 같은 문제가 생기기도 한다.
> renderToString은 React에서 SSR을 구현하는데 사용되는 method이다. 그런데 이 메소드는 스택을 막고  
> 동기적으로 처리된다. 이게 실행될 동안 서버는 멈추게 되는데 CSR은 클라이언트에서 거의 모든것을하기 때문에  
> 서버 자원을 덜 사용한다.