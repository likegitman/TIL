# Interface

1. 인터페이스는 일반적으로 타입 체크를 위해 사용되며 변수, 함수, 클래스에 사용할 수 있다
2. 인터페이스는 프로퍼티와 메소드를 가질 수 있다는 점에서 클래스와 유사하나  
   직접 인스턴스를 생성할 수 없고 모든 메소드는 추상 메소드이다.  
   단, 추상 클래스의 추상 메소드와 달리 abstract 키워드를 사용하지 않는다.

* 기존 JavaScript
```javascript
let user:object = {
    name: "unrin",
    age: 18,
}
console.log(user.age); // possible
```

* TypeScript
```javascript
// 기존 JS처럼 선언하고 접근하면 오류가 생기는데
// 이럴 때 사용하는 것이 interface
interface User {
    name: string;
    age: number;
}

let user:User = {
  name: "unrin",
  age: 18,
}

console.log(user.age);
```

# Declaration

```javascript
interface 이름 {
    key: type;
    key: type;
}
```

# Union, Optional, Readonly, Index, Function

### union
기본 type
```javascript
interface User {
    name: string;
    age: number;
    student: boolean;
}

let user:User = {
  name: "unrin",
  age: 18,
  student: false,
}
```

### optional
있어도 되고 없어도 되는 속성으로 만듦(? 사용)    
```javascript
interface User {
    name: string;
    age: number;
    gender?: string; // optional
}

let user:User = {
  name: "unrin",
  age: 18,
  // gender를 선언하지 않아도 오류가 생기지 않음
}
```

### readonly
읽기전용 속성으로 만듦(처음 생성할 때만 할당이 가능하고 후에는 재할당이 불가능)
```javascript
interface User {
    name: string;
    age: number;
    gender?: string
    readonly birthday: string; // readonly
}

let user:User = {
  name: "unrin",
  age: 18,
  gender: "male",
  birthday: "2000.01.01",
}

user.birthday="2000.01.02"; // error
```

### index
여러 속성 정보를 받을 때 사용 (key:number, value:string)
```javascript
interface User{
    name: string;
    age: number:
    gender?: string;
    readonly birthday: string; 
    [grade:number]: string;
}

let user:User = {
  name: "unrin",
  age: 18,
  gender: "male",
  birthday: "2000.01.01",
  1: "A",
  2: "B",
}
```

### function
> 함수의 매개변수와 리턴 값의 type을 지정할 때 사용
```javascript
interface Add {
    (num1: number, num2: number): number;
}

const add: Add = (x, y) => {
    return x + y;
};

add(10, 20);

interface Adult {
    (age: number): boolean;
}

const isAdult: Adult = (age) => {
    return age > 19;
};

isAdult(20);
```

# Different from Type
## 공통점
> 둘 다 Object의 모양을 결정할 수 있다.

## 차이점
> interface는 오로지 Object의 모양을 TS에게 설명해 주기 위한 키워드  
> 이러한 이유로 type이 interface보다 할 수 있는 작업이 많다.

1. Type alias 만들기
```javascript
type Hello = string; // possible
interface Hello = string; // error
```

2. 특정 값으로 제한
```
type Team = "red" | "blue" | "yellow";
type Health = 1 | 5 | 10;
```
