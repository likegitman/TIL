# Declaration

## const (Immutable data)
> 변하지 않는 상수를 선언할 때 사용한다.  
> `const PI = 3.14`

## let (Mutable  data)
> 변할 수 있는 값을 선언할 때 사용한다.  
> 단, 변수의 값을 재할당 할 때는 let을 빼고 변수의 이름만 선언하고 할당해야한다.
```js
let name = 'Minsu';
name = 'Woonrin';
```

## var
> let과 똑같이 변할 수 있는 값을선언할 때 사용한다.  
> 변수를 어디에 선언했냐에 상관없이 항상 제일 위로 선언을 끌어올려준다.  
> 참고 : [hoisting](/JAVASCRIPT/hoisting.md)  
> 즉, 할당을 먼저하고 나중에 var를 선언해도 호출이 된다.
```js
name='Woonrin';
var name;
```

# 정리
> const와 let, var의 차이점은 const는 값이 변할 수 없고 let과 var는 값이 변할 수 있다.

> let과 var의 차이점은 let은 선언하기 전에 미리 할당할 수 없고  
> var는 선언하기 전에 미리 할당할 수 있다.
