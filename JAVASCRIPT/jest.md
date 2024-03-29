# JEST
> JavaScript Test의 약자로 JS코드가 제대로 동작하는지를 확인하는 test case를 만드는 테스팅 프레임워크이다.
> lint가 코드 스타일에 규칙을 정하는 것이라면 jest는 코드가 올바른 기능을 하는 지 체크할 수 있다.  

## Example
```js
const sum = require('./sum')

test('1 + 2는 3입니다.', () => {
  expect(sum(1, 2)).toBe(3)
})
```

## Matchers
> 테스트 코드에서 기대하는 결과를 검증하기 위해 사용되는 함수이며 테스트 대상 코드의  
> 실행 결과나 값을 기대하는 값과 비교하여 일치 여부를 판단하는 역할을 한다.  
> Jest는 다양한 Matcher 함수를 제공하여 다양한 종류의 테스트 검증을 수행할 수 있도록 도와준다.

### toBe(value)
> 기본 값을 비교하거나 개체 인스턴스의 참조 ID를 확인하는 데 사용한다.  
> `toBe(value)`는 값과 타입(데이터 유형)을 모두 바교한다.  
> 그렇기에 값과 타입이 정확하게 일치해야 테스트가 성공한다.
```js
const User = {
  name: 'Mike',
  age: 25,
};

describe('The User', () => {
  test('User의 나이는 25입니다. ', () => {
    expect(User.age).toBe(25);
  }); // 성공

  test('User의 이름은 Mike입니다.', () => {
    expect(User.name).toBe('Mike');
  }); // 성공

  test('이름은 Mike입니다.', () => {
    expect({ name: 'Mike' }).toBe({ name: 'Mike' });
  }); // 실패 (내요이 같아도 서로 다른 메모리이다.)
});
```

### toEqual(value)
> 개체 인스턴스의 모든 속성을 재귀적으로 비교하는 데 사용한다. 값이 일치하는지 비교한다는 점에서  
> `toBe(value)`와 헷갈릴 수 있지만 `toEqual(value)`은 값의 내용(값 자체)을 비교한다.  
```js
const User1 = {
  name: 'Jane',
  age: 20,
};
const User2 = {
  name: 'Jane',
  age: 20,
  gender: undefined
};

describe('The User', () => {
  test('User1의 값과 User2의 값이 일치한다.', () => {
    expect(User1).toEqual(User2);
  }); // 성공

  test('User1의 값과 User2의 값이 일치한다.', () => {
    expect(User1).toStrictEqual(User2);
  }); // 실패
});
```

### [더 많은 Matchers](https://jestjs.io/docs/using-matchers)

## 비동기
### Calback
#### 함수 파일
```js
const fn = {
  getName: (callback) => {
    const name = 'Woonrin'
    setTimeout(() => {
      callback(name)
    }, 2000)
  }
}

module.exports = fn
```

#### 테스트 파일
> done은 Jest에게 테스트할 코드가 비동기 코드라는 것을 알려주며 콜백의 호출까지  
> 마무리가 되었다(done)는 것을 알려주는 것이다.
```js
const fn = require('./fn')

// done을 호출하지 않으면 test는 빠르게 통과되어 모든 test가 정답이라고 처리한다.
describe('The Callback', () => {
  test('2초 후에 받아오는 나이는 20살입니다.', (done) => {
    function callback(name) {
      try {
        expect(name).toBe('Woonrin')
        done()
      } catch (e) {
        done(e)
      }
    }
    fn.getName(callback)
  }) 
});
```

### Promise
#### 함수 파일
```js
const fn = {
  getAge: () => {
    const age = 20
      return new Promise((resolve, reject) => {
        setTimeout(() => {
          resolve(age)
        }, 2000)
      })
  }
}

module.exports = fn
```

#### test 파일
##### then catch
```js
const fn = require('./fn')

describe('The Async', () => {
  test('2초 후에 받아오는 나이는 20살입니다.', () => {
    return fn.getAge().then((age) => {
      expect(age).toBe(20)
    })
  }) 
});
```

##### async, await
```js
const fn = require('./fn')

describe('The Async', () => {
  test('2초 후에 받아오는 나이는 20살입니다.', async () => {
    const age = await fn.getAge()
    expect(age).toBe(20)
  }) 
});
```

## 전후 작업
> test를 하다보면 test 전 후에 해주어야 될 작업이 생기는데 이를 위해 Jest에서는 help 함수를 제공한다.

## Example
### beforeEach
> 각각의 테스트가 실행되기 전에 필요한 설정이나 값을 초기화하는 경우에 주로 사용되는 함수이다.
> beforeEach 블록 내에서 작성한 코드는 해당 테스트 내의 모든 테스트 케이스에 적용된다.
```js
const fn = require('./fn')

let num = 10

beforeEach(() => {
  num = 0
})

test('0 + 1은 1이다.', () => {
  num = fn.add(num, 1)
  expect(num).toBe(1)
})

test('0 + 2는 2다.', () => {
  num = fn.add(num, 2)
  expect(num).toBe(2)
})

test('0 + 3은 3이다.', () => {
  num = fn.add(num, 3)
  expect(num).toBe(3)
})

test('0 + 4는 4야.', () => {
  num = fn.add(num, 4)
  expect(num).toBe(4)
})
```
> 결과 : 모두 성공 beforeEach를 사용하지 않았다면 첫번째 테스트만 성공

### afterEach
> `beforeEach`는 모든 테스트 케이스 이전에 실행되지만 `afterEach`는 한 테스트가 끝날 때마다 실행되어서
> 한 테스트가 끝날 때마다 정리 작업을 할 때 많이 사용된다. 테스트가 끝날때마다 어떤 log를 보는것을
> 예로 들 수 있다.
```js
const fn = require('./fn')

let num = 10

afterEach(() => {
  num = 0
})

test('0 + 1은 1이다.', () => {
  num = fn.add(num, 1)
  expect(num).toBe(1)
})

test('0 + 2는 2다.', () => {
  num = fn.add(num, 2)
  expect(num).toBe(2)
})

test('0 + 3은 3이다.', () => {
  num = fn.add(num, 3)
  expect(num).toBe(3)
})

test('0 + 4는 4야.', () => {
  num = fn.add(num, 4)
  expect(num).toBe(4)
})
```
> 결과 : 첫 번째 테스트를 제외한 테스트 모두 성공 afterEach는 테스트가 끝날 때마다 실행되기 때문에
> 첫 번째 테스트에서 num은 초기화 되지않고 10인채 테스트를 진행한다.

## 테스트 제어
### only
> 특정 한 테스트 케이스만 실행하고 나머지는 무시한다. 보통 테스트가 통과가 되지 않았을 때
> 코드상의 오류인지 알아볼 때 사용한다. 아래 코드에서 `0 + 4는 4야`라는 테스트에서 오류가 발생한다.
> 이때 오류를 발생시키는 `num = 5`코드를 포함한 테스트를 skip하기 때문에 마지막 테스트는 통과된다.
```js
const fn = require('./fn')

let num = 0

test('0 + 1은 1이야', () => {
  expect(fn.add(num, 1)).toBe(1)
})

test('0 + 2는 2야', () => {
  expect(fn.add(num, 2)).toBe(2)
})

test.skip('0 + 3은 3이야', () => {
  expect(fn.add(num, 3)).toBe(3)
  num = 5
})

test.only('0 + 4는 4야', () => {
  expect(fn.add(num, 4)).toBe(4)
})
```
> 결과 : 마지막 테스트는 통과되고 마지막을 제외한 나머지는 테스트가 `skip`된다.

### skip
> 해당 테스트 케이스를 테스트하지않고 건너뛸 때 사용한다. test에서 오류가 발생했을 때 어떤 테스트가
> 원인인지 찾을 때 주로 사용한다. 또한 완성되지 않은 테스트를 건너뛸 때도 사용된다.
```js
const fn = require('./fn')

let num = 0

test('0 + 1은 1이야', () => {
  expect(fn.add(num, 1)).toBe(1)
})

test('0 + 2는 2야', () => {
  expect(fn.add(num, 2)).toBe(2)
})

test.skip('0 + 3은 3이야', () => {
  expect(fn.add(num, 3)).toBe(3)
  num = 5
})

test('0 + 4는 4야', () => {
  expect(fn.add(num, 4)).toBe(4)
})
```
> 결과 : 오류의 원인이 되는 테스트를 skip 했기에 skip한 테스트 제외 모두 통과된다.

## Snapshot
> 특정 코드, 컴포넌트의 현재 상태나 출력을 저장하고 이후 테스트 중 이 상태를 기준으로
> 예상 결과와 비교하는 도구이다. 주로 코드 또는 UI 컴포넌트의 렌더링 결과가 예상한대로
> 유지되는지 확인하고 변경 사항을 감지하는데에 사용된다.
