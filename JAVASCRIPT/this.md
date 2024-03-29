# this
> 자신이 속한 객체 또는 자신이 생성할 인수턴스를가리키는 자기 참조 변수이다.  
> 이 this를 통하여 자신이 속한 객체 또는 자신이 생성할 인스턴스의 프로퍼티나 메서드를  
> 참조할 수 있다. 자바스크립트에서 this는 '누가 나를 불렀느냐'를 뜻한다고 한다.  
> 이 말은 선언이 아닌 호출에서 따라 값이 달라진다는 것이다.

### this 바인딩
> 식별자와 값을 연결하는 과정을 말한다.
> 변수 선언은 변수 이름과 확보된 메모리 공간의 주소를 바인딩하는 것이다.
> this 바인딩은 this와 this가 가리킬 객체를 바인딩하는 것이다.

# 단독 this
```javascript
let a = this;
console.log(a); // window
```
> 위 코드는 그저 this를 호출하기 때문에 브라우저 기준에서  
> global object인 [object Window]를 가리킨다.

# 함수 this
```javascript
function printThis() {
  return this;
}

console.log(printThis()); // window
```
> 위 코드에서 this는 함수의 주인에게 바인딩 되는데  
> 함수의 주인은 window객체이다.

```javascript
let num = 0;

function addNum() {
    this.num = 100;
    num++;

    console.log(num); // 101
    console.log(window.num); // 101
    console.log(num === window.num) // true
}

addNum();
```
> 위 코드에서 this.num은 window객체를 가리키는데  
> 따라서 num은 전역변수를 가리키게 된다.

## Strict Mode (엄격 모드)
```javascript
function printThis() {
  return this;
}

console.log(printThis()); // undefined
```
> 함수 내부 this에 디폴트 바인딩이 없기 때문에 undefined가 나타난다.

```javascript
let num = 0;

function addNum() {
    this.num = 100; //ERROR! Cannot set property 'num' of undefined
    num++;
}

addNum();
```
> 오류가 나는 이유는 위와 같은 이유로 this.num은 undefined.num을 한 것과 똑같기 때문에  
> 오류가 발생한다.

# 메서드 this
```javascript
let Person = {
  firstName: 'Lee',
  lastName: 'Woonrin',
  fullName: function () {
    return this.firstName + ' ' + this.lastName;
  },
};
 
Person.fullName(); //"Lee Woonrin"
```
> 위 콛에서 메서드 호출 시 메서드 내부 코드에서 사용된 this는  
> 해당 메서드를 호출한 객체로 바인딩된다.

```javascript
let num = 0;
 
function showNum() {
  console.log(this.num);
}
 
showNum(); //0
 
let obj = {
  num: 200,
  func: showNum,
};
 
obj.func(); //200
```
> 위 코드에서 함수 내의 this는 window객체를 가리키고있기 때문에 전역변수인 num이 나타나게된다.  
> 그와 달리 메서드 내의 this는 호출한 객체를 가리키기에 200이 찍히게된다.

# EventListener this
```javascript
const radio = document.querySelector("input");
radio.addEventListener("change", function thisShow(event) {
  console.log(this);
})
```
> EventListener 안에서의 this는 event.currentTarget을 가리킨다.  
> 여기서 event.currentTarget은 이벤트가 동작하는 곳을 나타낸다.
