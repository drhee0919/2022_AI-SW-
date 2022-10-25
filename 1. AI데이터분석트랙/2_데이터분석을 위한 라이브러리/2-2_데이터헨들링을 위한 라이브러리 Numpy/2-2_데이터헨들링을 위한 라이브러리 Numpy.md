### 2-2. 데이터헨들링을 위한 라이브러리 Numpy

**Q. 다음 중 파이썬 NumPy에 대한 설명으로 옳은 것을 모두 고르세요. (정답 : 3개)**

1. NumPy는 Python에서 대규모 다차원 배열을 다룰 수 있게 도와주는 라이브러리이다.(O)
2. 파이썬 리스트에 비해서는 상대적으로 느린 연산을 지원하고 있는 것이 단점이다.(X)
3. NumPy를 사용할 경우, 반복문 없이 배열 처리 할 수 있다.(O)
4. NumPy를 활용하여 데이터를 처리할 경우, 파이썬 리스트에 비해서는 메모리를 효율적으로 사용할 수 있다.(O)

```
파이썬 리스트에 비해서 상대적으로 빠른 연산을 지원하고 있는 것이 장점이다.
```



**배열 만들기**

> * Numpy 라이브러리는 효율적인 데이터분석이 가능하도록 N차원의 배열 객체를 지원합니다
> * Numpy의 배열은 파이썬의 `list()`보다도 빠른 연산과 효율적인 메모리 사용이 가능하기 때문에 빅데이터 분석 등에 널리쓰이는 매우 강력한 라이브러리라고 할 수 있습니다.

```python
import numpy as np

# 0부터 4까지 연속적인 숫자가 들어있는 배열을 만들어 봅시다!
array = np.array(range(5)) # range(5)를 이용하여 0~4의 시퀀스를 만들어봅시다.
print(array)
```



**배열의 기초**

- ndarray의 속성

> * Numpy 라이브러리의 ndarray에는 배열의 여러 정보를 나타내는 속성값을 담고 있는데요, `ndim`, `shape`, `size`, `dtype` 등이 있습니다.

```python
import numpy as np

print("1차원 array")
array = np.array(range(10))
print(array)

# 1. type()을 이용하여 array의 자료형을 출력해보세요.
print(type(array))

# 2. ndim을 이용하여 array의 차원을 출력해보세요.
print(array.ndim)

# 3. shape을 이용하여 array의 모양을 출력해보세요.
print(array.shape)

# 4. size를 이용하여 array의 크기를 출력해보세요.
print(array.size)

# 5. dtype을 이용하여 array의 dtype(data type)을 출력해보세요.
print(array.dtype)

# 6. array의 5번째 요소를 출력해보세요. (array[5])
print(array[5])

# 7. array의 3번째 요소부터 5번째 요소까지 출력해보세요. (array[3:6])
print(array[3:6])
```

- 2차원 배열의 속성

> * matrix를 통해 2차원 배열을 만들 수 있다. 

```python
import numpy as np


print("2차원 array")
matrix = np.array(range(1,16))  #1부터 15까지 들어있는 (3,5)짜리 배열을 만듭니다.
matrix.shape = 3,5
print(matrix)


# 1. type을 이용하여 matrix의 자료형을 출력해보세요.
print(type(matrix))

# 2. ndim을 이용하여 matrix의 차원을 출력해보세요.
print(matrix.ndim)

# 3. shape을 이용하여 matrix의 모양을 출력해보세요.
print(matrix.shape)

# 4. size를 이용하여 matrix의 크기를 출력해보세요.
print(matrix.size)

# 5. dtype을 이용하여 matrix의 dtype(data type)을 출력해보세요.
print(matrix.dtype)

# 6. astype을 이용하여 matrix의 dtype을 str로 변경하여 출력해보세요.
print(matrix.astype('str'))

# 7. matrix의 (2,3) 인덱스의 요소를 출력해보세요.
print(matrix[2,3])

# 8. matrix의 행은 인덱스 0부터 인덱스 1까지 (0:2), 열은 인덱스 1부터 인덱스 3까지 (1:4) 출력해보세요.
print(matrix[0:2, 1:4])
```



**Indexing&Slicing**

> * 배열의 인덱스를 활용하여 값을 찾아내거나 배열의 일부분을 가져올 수 있습니다. 이를 **Indexing & Slicing**이라 합니다.
> * Boolean mask를 이용하여 원하는 값을 추출하는 것은 **Boolean indexing**이라 합니다.
> * 배열의 각 요소 선택을 Index 배열을 전달하여 지정하는 방식은 **Fancy indexing**이라 합니다.

```python

import numpy as np

matrix = np.arange(1, 13, 1).reshape(3, 4)
print(matrix)
# matrix는 아래와 같습니다.
# [[ 1  2  3  4]
#  [ 5  6  7  8]
#  [ 9 10 11 12]]

# 1. Indexing을 통해 값 2를 출력해보세요.
answer1 = matrix[0, 1] # 2는 0행 1열에 있습니다.

# 2. Slicing을 통해 매트릭스 일부인 9, 10을 가져와 출력해보세요.
answer2 = matrix[2:, :2] # 2행 첫 두 개 열에 9, 10 이 있습니다. (2:, :2)

# 3. Boolean indexing을 통해 5보다 작은 수를 찾아 출력해보세요.
answer3 = matrix[matrix < 5]

# 4. Fancy indexing을 통해 두 번째 행만 추출하여 출력해보세요.
answer4 = matrix[[1]] # 두번째 행의 인덱스는 1입니다.

# 위에서 구한 정답을 출력해봅시다.
print(answer1)
print(answer2)
print(answer3)
print(answer4)  
```

