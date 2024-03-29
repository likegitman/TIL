# Compiler
프로그램 전체를 탐색하여 이를 모두 기계어로 번역한다. 프로그램 전체를 탐색하기 때문에 초기 탐색 시간이 오래걸린다.

하지만 전체적인 실행 시간만 본다면 인터프리터보다 빠르다. 이런 이유는 초기 탐색을 끝내면 실행파일을 만들어놓고

다음에 실행할 때 만들어놓은 실행 파일을 실행하기 때문이다. 대신 컴파일러는 고급언어로 작성된 소스를 기계어로

번역하고 이 과정에서 Object Code라는 파일을 만드는데 이것을 묶어서 하나의 실행 파일로 다시 만드는 Linking이라는

작업을 해야한다. 그래서 평균적으로 인터프리터보다 많은 메모리를 사용한다는 단점이 있다. 컴파일러는 오류 메시지를

생성할 때 전체 코드를 검사한 후에 오류 메시지를 생성한다. 따라서 코드 실행 전에 오류를 발견할 수 있다.

컴파일러를 사용하는 대표적인 언어들로는 C, C++, JAVA 등이 있다.

# Interpreter
컴파일러와 반대로 인터프리터는 포로그램을 실행할 때 한 번에 한 문장씩 번역한다. 그렇기에 한 번에 전체를 탐색하고

실행파일을 만들어서 실행하는 컴파일러보다 실행시간이 더 오래걸린다. 하지만 컴파일러에서 단점이였던 메모리면에서는

효율이 좋다. 컴파일러처럼 목적코드를 만들지도 않고 Linking 과정도 거치지 않기 때문이다. 따라서 컴파일러보다

메모리 사용에 더욱 효율적인 모습을 보여준다. 오류 메시지를 생성하는 방식도 컴파일러와 다르다. 한 번에 한 문장씩만

번역하기 때문에 프로그램을 실행시키고 한 문장씩 번역될 때 오류를 발견하면 즉시 프로그램을 중지한다.

그래서 프로그램을 실행한 후에 오류 발견이 가능해진다. 인터프리터를 사용하는 대표적인 언어들로는

Python, Ruby, Javascript 등이 있다.
