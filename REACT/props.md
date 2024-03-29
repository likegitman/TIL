# Props
> 부모 컴포넌트에서 자식 컴포넌트로 전달해 주는 데이터이다.(읽기 전용 데이터)  
> 읽기 전용 데이터이기 때문에 자식 컴포넌트에서 props를 변경할 수 없고 props를 전달해준  
> 부모 컴포넌트만 바꿀 수 있다.
  
# 부모에서 값 지정
  
## App.js
```javascript
import MyComponent from "./MyComponent";

function App() {
  return (
    <div>
      <MyComponent name='woonrin' />
    </div>
  );
}

export default App;

```
  
## MyComponent.js
```javascript
function MyComponent({name}) {
    return(
        <div>
            안녕하세요, 제 이름은 {name}입니다.
        </div>
    );
};

export default MyComponent;
```
  
# defaultProps

## App.js
```javascript
import MyComponent from "./MyComponent";

function App() {
  return (
    <div>
      <MyComponent />
    </div>
  );
};

export default App;

```

## MyComponent.js
```javascript
function MyComponent({name}) {
    return(
        <div>
            안녕하세요, 제 이름은 {name}입니다. <br />
        </div>
    );
};

MyComponent.defaultProps={
    name: 'woonrin'
};

export default MyComponent;
```
  
# children
> 컴포넌트 태그 사이의 내용

## App.js
```javascript
import MyComponent from "./MyComponent";

function App() {
  return (
    <div>
      <MyComponent>리액트</MyComponent>
    </div>
  );
};

export default App;

```

## MyComponent.js
```javascript
function MyComponent(props)=>{
    return(
        <div>
            안녕하세요, 제 이름은 {props.name}입니다. <br />
            children 값은 {props.children}입니다.
        </div>
    );
};

MyComponent.defaultProps={
    name: 'woonrin'
};

export default MyComponent;
```

# 비구조화 할당 문법

## App.js
```javascript
import MyComponent from "./MyComponent";

function App() {
  return (
    <div>
      <MyComponent>리액트</MyComponent>
    </div>
  );
};

export default App;

```

## MyComponent.js
```javascript
function MyComponent(props) {
    // 비구조화 할당 문법
    const {name, children}=props;

    return(
        <div>
            안녕하세요, 제 이름은 {name}입니다. <br />
            children 값은 {children}입니다.
        </div>
    );
};

MyComponent.defaultProps={
    name: 'woonrin'
};

export default MyComponent;
```

## MyComponent.js(2)
```javascript
const MyComponent=({name, children})=>{

    return(
        <div>
            안녕하세요, 제 이름은 {name}입니다. <br />
            children 값은 {children}입니다.
        </div>
    );
};

MyComponent.defaultProps={
    name: 'woonrin'
};

export default MyComponent;
```

# propTypes

## App.js
```javascript
import MyComponent from "./MyComponent";

const App=()=>{
  return (
    <div>
      <MyComponent name='woonrin'>리액트</MyComponent>
    </div>
  );
}

export default App;

```

## MyComponent.js
```javascript
import PropTypes from "prop-types"; 

function MyComponent({name, children}){

    return(
        <div>
            안녕하세요, 제 이름은 {name}입니다. <br />
            children 값은 {children}입니다.
        </div>
    );
};

MyComponent.defaultProps={
    name: '기본이름'
};

MyComponent.propTypes={
    // prop의 타입을 지정
    name: PropTypes.string
};

export default MyComponent;
```

# isRequired
> propTypes를 지정하지 않았을 때 경고 메시지 출력

## App.js
```javascript
import MyComponent from "./MyComponent";

function App() {
  return (
    <div>
      <MyComponent name="woonrin" favoriteNum={7}>
        리액트
      </MyComponent>
    </div>
  );
};

export default App;


```

## MyComponent.js
```javascript
import PropTypes from "prop-types"; 

function MyComponent({name, favoriteNum,children}) {

    return(
        <div>
            안녕하세요, 제 이름은 {name}입니다. <br />
            children 값은 {children}입니다. <br />
            제가 좋아하는 숫자는 {favoriteNum}입니다.
        </div>
    );
};

MyComponent.defaultProps={
    name: '기본이름'
};

MyComponent.propTypes={
    name: PropTypes.string,
    // App.js에서 지정하지 않았다면 console창에 경고 메시지 출력
    favoriteNum: PropTypes.number.isRequired
};

export default MyComponent;
```

# 다양한 PropTypes 종류
* array : 배열
* arrayOf(다른 PropType) : 특정 PropType으로 이루어진 배열을 의미,  
  예를 들어 arrayOf(PropTypes.number)는 숫자로 이루어진 배열
* bool : true 혹은 false 값
* func : 함수
* number : 숫자
* object : 객체
* string : 문자열
* symbol : ES6의 symbol
* node : 렌더링할 수 있는 모든 것(숫자, 문자열, 혹은 JSX코드, children도 node PropType이다.)
* instanceOf(클래스) : 특정 클래스의 인스턴스( ex) instanceOf(MyClass) )
* oneOf(['dog', 'cat']) : 주어진 배열 요소 중 값 하나
* oneOfType([React.PropTypes.string, PropTypes.number]) : 주어진 배열 안의 종류 중 하나
* objectOf(React.PropTypes.number) : 객체의 모든 키 값이 인자로 주어진 PropType인 객체
* shape({ name: PropTypes.string, num: PropTypes.number }) : 주어진 스키마를 가진 객체 
* any : 아무 종류
