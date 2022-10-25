### 2-1. Python의 여러가지 모듈과 패키지



**Q. 다음 중 모듈에 대한 설명으로 옳지 않은 것은?** 

1. 모듈이 필요한 상황은 코드의 길이가 길어지는 상황이다.(O)
2. 모듈은 특정 목적을 가진 함수, 자료의 모임이라고 할 수 있다.(O)
3. 모듈은 반드시 본인이 직접 제작하여 사용해야 한다.(X)

```
모듈을 활용하는 이유는 누군가 만들어놓은 함수와 변수를 활용하기 위함이기도 합니다.
예를 들어, 다양한 랜덤값 생성과 관련된 함수가 모여있는 `random` 모듈은 직접 구현하지 않아도 사용이 가능합니다.
```



**계산기 모듈 만들기**

```python
## main.py
## 이렇게 해보세요!를 따라 수행해보세요.
import cal

var1 = cal.modelName # cal.modelName을 var1에 저장하세요.

var2 = cal.plus(3, 4) # cal.plus를 활용하여 3+4를 구해보세요.

var3 = cal.minus(7, 2) # cal.minus를 활용하여 7-2를 구해보세요.

## 변수의 값을 확인하는 출력문입니다.
print(var1, var2, var3)
```

```python
## cal.py
def plus(a, b):
    return a+b # a+b 를 반환하세요.

def minus(a, b):
    return a-b # a-b 를 반환하세요.

modelName = 'ELI-C2' # "ELI-C2" 를 modelName에 저장하세요.

```



**모듈 불러오기**

- 모듈을 불러오는 방법

> * `from a import b` <br>a 모듈(혹은 패키지)에서 b 함수를 가져오겠다. b를 사용하기 위해선 **b() 꼴** 로 사용 가능
> * import a <br>a 모듈을 불러오겠다. a 모듈 안에있는 b 함수를 사용하기 위해선 **a.b()** 꼴로 사용해야함

```python
## random과 math를 다르게 불러오는 방법을 배워봅시다.
## 이렇게 해보세요!를 따라 수행해보세요.
from random import randrange # from, import를 활용하여 random 모듈에서 randrange 함수를 불러오세요.
import math # math 모듈을 불러오세요.

var1 = randrange(1, 11)
var2 = math.log(5184, 72) # math.log 함수를 사용해보세요.
```



- 웹페이지 구성 확인하기 

> * Python에서는 쉽게 웹페이지의 정보를 가져올 수 있는 `urllib`패키지를 제공합니다. 
> * 이 중에서 `urllib.request.urlopen` 함수는 해당 url의 `html` 파일을 가져옵니다.

```python
## https://en.wikipedia.org/wiki/Lorem_ipsum 홈페이지의 정보를 가져옵시다.
## 이렇게 해보세요!를 따라 수행해보세요.
from urllib._______ import _______ # url 패키지의 request 모듈에서 urlopen 함수를 불러오세요.

webpage = urlopen("https://en.wikipedia.org/wiki/Lorem_ipsum").read().decode("utf-8")

print(webpage)
```

