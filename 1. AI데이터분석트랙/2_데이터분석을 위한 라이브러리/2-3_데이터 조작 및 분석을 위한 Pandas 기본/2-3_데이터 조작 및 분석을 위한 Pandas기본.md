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



**데이터프레임 데이터 선택 및 변경하기**

- 조건에 충족하는 값 추출

> * 데이터 프레임에서, 각 컬럼마다 조건을 충족하는 값만 추출할 수 있습니다.
> * Numpy의 마스킹 연산처럼 조건식을 직접 쓸 수도 있고, `query()` 함수를 이용하는 방법도 있습니다. 

```python
import numpy as np
import pandas as pd

print("Masking & query")
df = pd.DataFrame(np.random.rand(5, 2), columns=["A", "B"])
print(df, "\n")

# 데이터 프레임에서 A컬럼값이 0.5보다 작고 B컬럼 값이 0.3보다 큰값들을 구해봅시다.
# 마스킹 연산을 활용하여 출력해보세요!
print(df[(df['A'] < 0.5 ) & (df['B'] > 0.3)])

# query 함수를 활용하여 출력해보세요!
print(df.query("A<0.5 and B>0.3")) # "A<0.5 and B>0.3" 쿼리를 사용하세요.
```

- 새로운 컬럼 추가하기

> * 아래 `국가별 GDP` 시리즈 데이터와 `국가별 인구` 시리즈 데이터를 이용해 만든 `country` 데이터프레임이 준비되어 있습니다.
> * **1인당 GDP** 를 나타내는 새로운 컬럼인 `gdp per capita`를 데이터 프레임에 추가해봅시다.

**Indexing&Slicing**

> * 배열의 인덱스를 활용하여 값을 찾아내거나 배열의 일부분을 가져올 수 있습니다. 이를 **Indexing & Slicing**이라 합니다.
> * Boolean mask를 이용하여 원하는 값을 추출하는 것은 **Boolean indexing**이라 합니다.
> * 배열의 각 요소 선택을 Index 배열을 전달하여 지정하는 방식은 **Fancy indexing**이라 합니다.

```python
import numpy as np
import pandas as pd

# GDP와 인구수 시리즈 값이 들어간 데이터프레임을 생성합니다.
population = pd.Series({'korea': 5180,'japan': 12718,'china': 141500,'usa': 32676})
gdp = pd.Series({'korea': 169320000,'japan': 516700000,'china': 1409250000,'usa': 2041280000})
print("Country DataFrame")
country = pd.DataFrame({"population" : population,"gdp" : gdp})
print(country)


# 데이터프레임에 gdp per capita 칼럼을 추가하고 출력합니다.
gdp_per_pop = country["gdp"] / country["population"] # gdp에서 population을 나눠 1인당 gdp를 구합니다.
country["gdp per capita"] = gdp_per_pop
print(country)
```

