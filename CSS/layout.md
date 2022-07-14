# Layout

## div
> 기본적으로 block 값이어서 한 줄에 하나씩 나옴

## span
> 기본적으로 inline 값이어서 한 줄에 여러개가 나옴

## display
> 기본 값 변경이 가능 함
* block
> 한 줄에 하나씩 나옴
* inline
> 한 줄에 여러개가 나옴
* inline-block
> 한 줄에 block 값들이 여러개가 나오게 할 수 있음

## position
* static (기본 값)
> HTML에 정의된 순서대로 브라우저에 자연스레 출력 됨
* relative
>  원래 있어야 되는 자리에서 상대적으로 위치변경이 일어 남( px값 만큼 움직임 )
* absolute
> 자신의 아이템과 가장 가까이 있는 박스안에서 위치변경이 일어 남
* fixed
> 박스안에서 완전히 벗어나 웹페이지 안에서 위치변경이 일어 남
* sticky
> 원래 있어야 되는 자리에 있으면서 스크롤링이 일어나도 사라지지 않음