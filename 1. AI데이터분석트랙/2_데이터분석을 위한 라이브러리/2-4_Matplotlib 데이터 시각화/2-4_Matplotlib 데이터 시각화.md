### 2-4. Matplotlib 데이터 시각화

**선 그래프**

> * Matplotlib으로 그릴 수 있는 여러가지 그래프 중 선 그래프(Line Graph)를 직접 그려봅시다.
> * **속성(linestyle, marker, color) 값**을 변경하여 그래프를 그리는 다양한 방법에 대해서 알아봅시다.

```python
from elice_utils import EliceUtils
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

elice_utils = EliceUtils()

#이미 입력되어 있는 코드의 다양한 속성값들을 변경해 봅시다.
x = np.arange(10)
fig, ax = plt.subplots()
ax.plot(
    x, x, label='y=x',
    linestyle='-', # 실선 (-) 으로 변경해보세요.
    marker='.', # 점 (.) 으로 변경해보세요.
    color='blue'
)
ax.plot(
    x, x**2, label='y=x^2',
    linestyle='-.', # 대시점선 (-.) 으로 변경해보세요.
    marker=',', # 픽셀 (,)로 변경해보세요.
    color='red'
)
ax.set_xlabel("x")
ax.set_ylabel("y")

# elice에서 그래프를 확인
fig.savefig("plot.png")
elice_utils.send_image("plot.png")
```

![image_output](.\image_output.png)

**히스토그램 그리기**

- 선언순서 확인하기 

```python
'''
먼저, 도화지를 그리듯 그래프를 그리기 위한 fig와 ax를 설정합니다. : fig, ax = plt.subplots()
그 후, 히스토그램으로 시각화 하고자 하는 데이터를 설정합니다. : data = np.random.randn(1000)
이후, 히스토그램 그래프로 시각화합니다. : ax.hist(data, bins=50)
'''

fig, ax = plt.subplots() ##subplots
data = np.random.randn(1000) ##data
ax.hist(data, bins=50) ##hist
```

![hitogram_graph](.\hitogram_graph.png)

- 막대 그래프와 히스토그램 그리기

> * Bar그래프(막대형 차트)는 여러 값을 비교하는데 적합합니다. 여러개의 값을 입력 받고 그 값들을 한눈에 비교 할 수 있습니다.
> * Histogram은 일정 시간 동안의 숫자 데이터 분포를 시각화 하는데 적합합니다.
> * 아래 `x`와 `y` 데이터는 각 스포츠의 종목과, 선호하는 학생의 수를 조사한 결과입니다.
> * `z` 데이터는 1000개의 정규분포 난수를 담고 있습니다.
> * z 데이터를 **등급**을 50개로 나눈 히스토그램으로 출력해봅니다.

```python
from elice_utils import EliceUtils
elice_utils = EliceUtils()
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import matplotlib.font_manager as fm

'''matplotlib 의 pyplot으로 그래프를 그릴 때, 기본 폰트는 한글을 지원하지 않습니다. 아래는 한글을 지원하는 나눔바른고딕 폰트로 바꾼 코드입니다.'''
fname='./NanumBarunGothic.ttf'
font = fm.FontProperties(fname = fname).get_name()
plt.rcParams["font.family"] = font
'''위 코드 덕분에, 막대 그래프에서 축구, 야구, 농구, 배드민턴, 탁구가 올바르게 출력되었습니다.'''

# Data set
x = np.array(["축구", "야구", "농구", "배드민턴", "탁구"])
y = np.array([13, 10, 17, 8, 7]) # [13, 10, 17, 8, 7] 로 변경해보세요.
z = np.random.randn(1000)

'''아래 코드는, 하나의 도화지(figure)에
1*2의 모양으로 그래프를 그리도록 합니다. 즉, 그래프를 2개 그리고, 가로로 배치한다는 의미입니다.'''
fig, axes = plt.subplots(1, 2, figsize=(8, 4)) 

# axes[0]은 막대 그래프를, axes[1]은 히스토그램을 그립니다.
# Bar 그래프
axes[0].bar(x, y)
# 히스토그램
axes[1].hist(z, bins = 50) # bins를 200으로 변경해보세요.


# elice에서 그래프 확인하기
fig.savefig("plot.png")
elice_utils.send_image("plot.png")
```

> - 50개로 나눴을 때(bins=50)

![bins=50](.\bins=50.png)

> * 200개로 나눴을 때 

![bins=200](.\bins=200.png)

**그래프 범례**

> * 하나의 그래프에 여러 데이터를 한 번에 그리는 경우 각 데이터의 정보를 그래프에 함께 띄워 주어야 합니다. 이때 범례 함수( ax.legend() )를 사용합니다. 
> * 속성 값을 변경하여 범례(legend)의 모양을 다양하게 변경할 수 있습니다.

```python
## 그래프의 범례(legend) 속성 중 위치를 변경하여 봅시다: loc
from elice_utils import EliceUtils
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

elice_utils = EliceUtils()

x = np.arange(10)
fig, ax = plt.subplots()
ax.plot(
    x, x, label='y=x',
    linestyle='-',
    marker='.',
    color='blue'
)
ax.plot(
    x, x**2, label='y=x^2',
    linestyle='-.',
    marker=',',
    color='red'
)
ax.set_xlabel("x")
ax.set_ylabel("y")

#이미 입력되어 있는 코드의 다양한 속성값들을 변경해 봅시다.
ax.legend(
    loc='upper left', # center left 로 변경해보세요.
    shadow=True,
    fancybox=True,
    borderpad=2
)

# elice에서 그래프를 확인
fig.savefig("plot.png")
elice_utils.send_image("plot.png")
```

- loc = 'upper left' 설정시

![image_output2](.\image_output2-1.png)

- loc = 'center left' 설정시

![image_output2-2](E:.\image_output2-2.png)



