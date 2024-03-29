# React
> facebook에서 개발했고 사용자 인터페이스를 만들기 위한 JS의 라이브러리이다.

# 특징
1. Data Flow
> React는 단방향 데이터 흐름을 가진다. 다른 프레임워크인 AngularJS는 양방향 데이터 흐름을 가지고 있는데  
> 이런 데이터의 흐름은 규모가 커질수록 추적하기 힘들고 복잡해지는 경향이 있는데 React같이 단방향 데이터 흐름은  
> 규모가 크고 복잡해도 변화를 보다쉽게 예측할 수 있다.

2. Component 기반 구조
> React는 우리가 보는 화면 즉, UI를 component를 쪼개서 만든다.  
> 한 페이지 내에서도 다양한 부분을 독립된 컴포넌트들을 만들고 이것들을 조합해  
> UI를 구성한다. 이렇게 구분되어있으면 코드를 파악하는게 쉬워지고 재사용성이 높아진다.  
> 또, 컴포넌트 단위로 개발을하면 반복되는 코드를 일일이 칠 필요도 없고 import를 사용하기 때문에  
> 코드도 간결해지고 유지보수성이 높아진다.

3. Virtual DOM
> DOM은 html, css, javascript 등을 트리 형태로 인식하고 데이터를 객체로 관리한다.
> 이벤트가 발생할 때마다 Virtual DOM을 만들고, 또 업데이트 될 때는 실제 DOM과 비교한 다음  
> 이전과 현재 상태를 비교해 변경이 된 부분만 실제 DOM에 반영한다. Virtual DOM을 사용하면  
> 앱의 효율성과 속도를 개선할 수 있다.
