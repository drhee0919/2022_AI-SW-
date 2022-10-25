### 2-3. 데이터 조작 및 분석을 위한 Pandas 기본

**Series 데이터**

> * Series 데이터란 Numpy array가 보강된 형태로, Data와 index를 가지고 있는 데이터 형식입니다.
> * **딕셔너리**를 이용해서 인덱스와 값을 지정하여 Series 데이터를 직접 만들어봅시다.

```python
import numpy as np
import pandas as pd

# 예시) 시리즈 데이터를 만드는 방법.
# series = pd.Series([1,2,3,4], index = ['a', 'b', 'c', 'd'], name="Title")
# print(series, "\n")


# 국가별 인구 수 시리즈 데이터를 딕셔너리를 사용하여 만들어보세요.
country = pd.Series([ 5180, 12718, 141500, 32676], index = ['korea', 'japan', 'china', 'usa'], name="country")
print(country, "\n")
```



**데이터프레임**

> * 시리즈 데이터는 하나의 컬럼 값으로 이루어진 반면 **데이터 프레임**은 여러 개의 컬럼 값을 가질 수 있습니다.
> * **여러 개의 시리즈 데이터**를 이용하여 데이터 프레임을 만드는 법을 배워봅니다.

```python
import numpy as np
import pandas as pd

# 두 개의 시리즈 데이터가 있습니다.
print("Population series data:")
population_dict = {
    'korea': 5180,
    'japan': 12718,
    'china': 141500,
    'usa': 32676
}
population = pd.Series(population_dict)
print(population, "\n")

print("GDP series data:")
gdp_dict = {
    'korea': 169320000,
    'japan': 516700000,
    'china': 1409250000,
    'usa': 2041280000,
}
gdp = pd.Series(gdp_dict)
print(gdp, "\n")


# 이곳에서 2개의 시리즈 값이 들어간 데이터프레임을 생성합니다.
print("Country DataFrame")

country = pd.DataFrame({
    "population" : population,
    "gdp" : gdp
})
print(country)
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

