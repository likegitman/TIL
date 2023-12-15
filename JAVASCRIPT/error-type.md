# Compile Error
문법 오류인 Syntax Error 등에 해당 되는 오류이다. 또 다른 말로는 Parsing Error라고도 불린다.

이름처럼 컴파일 하는 동안에 발생하는 오류인데 다음과 같은 특징이 있다.
* 컴파일러/인터프리터가 소스 코드를 바이트 코드로 변환하면서 발견한 오류
* 컴파일 시에 에러 메시지로 오류의 위치를 알려주기 때문에 찾기 쉬운 오류
* 수정되지 않으면 프로그램은 컴파일 되지 않음

에러 메시지를 통해 런타임 에러보다 비교적 쉽게 해결할 수 있다.

컴파일 오류는 TypeScript를 사용한다면 js보다 많이 잡아주지만 항상 조심해야 된다.

# Runtime Error
컴파일 후 프로그램이 실행되는 동안에 발생하는 오류이다. 런타임 에러는 컴파일 에러보다 범위가 넓다.

보통 설계 미숙으로 인해 프로그램 실행 중 발생하며 어디서 발생한건지 컴파일에러보다 발견하기 어렵다.

종류
* NullPointerException (생성되지 않은 객체를 참조할 때 발생)
* Infinite Loop (무한 반복)
* ArithmeticException(0으로 숫자를 나눴을 때 발생)

런타임 에러는 2가지로 나눠지는데 논리 에러와 시스템 에러로 나눠진다.
* 논리 에러: 개발자의 논리적 실수에 의해 발생
* 시스템 에러: 프로그램 동작 중에 운영체제 또는 하드웨어에 문제가 발생하여 프로그램이 정상작동 하지 않을 때 발생