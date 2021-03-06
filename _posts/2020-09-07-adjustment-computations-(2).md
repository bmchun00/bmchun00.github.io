---
title: 표본과 모수
tag: 조정계산론
---

> 측정값을 분석하는 방법
>

2주차에서는 측정값을 수치적으로, 혹은 시각적으로 표현하는 방법에 대해서 학습합니다. 데이터들은 수치적인 방법과 시각적인 방법으로 표현이 가능한데요, 데이터와 마찬가지로 측정된 값들 역시 이러한 방법으로 표현이 가능합니다.

# Sample vs. Population
표본(Sample)과 모수(Population)에는 어떤 차이가 있을까요?

**모수(Population)** : 특정 값으로 만들 수 있는 모든 가능한 측정값입니다. (무한함)
**표본(Sample)** : 모집단에서 선택한 데이터의 부분 집합입니다.

# Range & Median
![](https://i.ibb.co/r0wjkJv/dataset.jpg)

다음과 같은 데이터 셋이 있다고 가정해봅시다.

* 우리는 이러한 데이터를 어떻게 정리해서 **더욱 의미있게** 만들 수 있을까요?
* 이 값들은 **합리적으로 예상한** 대표값인가요?
* 어떤 통계적 방법을 이용해야 이 데이터셋을 대표하고 분석할 수 있을까요?

![](https://i.ibb.co/QXqZCb1/dataset2.jpg)

이번엔 Table 2.1을 정렬한 Table 2.2가 있다고 가정해봅시다.

이러한 값들을 수치적으로 계산할 수 있습니다.

* **Range (범위)** : 최대값과 최소값의 차이
* **Median (중간값)** : 정렬된 값들의 가운데 값

# 데이터를 수치적으로 분석하는 방법
> 데이터셋에서 계산된 값들은 데이터의 정밀도나 정확도를 결정하는 데 사용됩니다.
>

수치적으로 데이터를 분석하는 방법은 크게 세 가지로 나눌 수 있습니다.
* **central tendency**
* **data variation**
* **relative standing**

이러한 세 가지를 **통계학** 이라고 부르며, 통계는 **샘플 데이터로 계산된** 수치적 분석 입니다.

**Measures of central tendency**

통계적인 값은 데이터 분포의 중심에 밀집하는 경향이 있습니다. (중심극한정리)

* **Arithmetic mean (산술평균)** : 우리가 자주 사용하는 평균값입니다. 데이터의 값을 모두 더하고 데이터의 수로 나눕니다.
* **Median (중간값)** : 정렬된 데이터 셋의 중간에 위치한 값을 의미합니다. (만약 데이터의 수가 짝수라면, 중간에 근사한 두 값들의 산술 평균을 구합니다.)
* **Mode (최빈값)** : 가장 자주 나타나는 값을 의미합니다. 성적에서 이러한 경향을 보인다고 합니다.

# 추가적 정의 (개념)
* **True values (참값) : μ** - 이론적으로 확실한 값
* **Error (오차) : ε = y - μ** - 측정값과 참값의 차이. 참값을 알아야 오차를 알 수 있습니다.
* **Most Probable Value (최확값) : Ȳ** - 측정된 값 중에서 가장 확률이 높다고 생각되는 값. 산술 평균 등이 있습니다.
* **Residual (잔차) : v = Ȳ - y** - 최확값과 측정된 값의 차이
* **Degrees of Freedom (자유도)** - 미지의 값을 결정하기 위해 측정된 횟수. 우리는  보통 n-1로서 자유도를 자주 볼 수 있었는데, 그 이유는 표본 표준편차에서는 '평균'이 절대적으로 정해져 있기 때문에 이 값을 뺀 나머지 n-1개가 계산으로부터 자유롭기 때문입니다.
* **Variance (분산)** - 데이터 셋의 **정밀도**를 평가할 수 있는 수치. 이때 모분산과 표본분산은 계산 과정이 다릅니다.

요약과 함께, 각 값을 구하는 수식은 다음과 같습니다.

![](https://i.ibb.co/1m7CcsJ/image.jpg)

Standard Error/Deviation 에는 +-기호가 붙어있다는 점에 유의합니다.

또한, 이 값을 MATLAB을 통해 구할 수 있는 수식은 다음과 같습니다.

![](https://i.ibb.co/SNBjCJm/image.jpg)

std()의 경우 함수의 flag를 통해 자유도를 구분할 수 있음에 유의합니다.

# 히스토그램을 이용한 분석
히스토그램을 이용하면, 다양한 항목을 분석해볼 수 있습니다.
* 데이터가 중앙 값에 대해 대칭인지 여부 **(symmetric)**
* 측정값의 범위 또는 분포 **(range)**
* 측정값의 발생 빈도 **(frequency)**
* 히스토그램의 가파른 정도 : 정밀도와 연관이 있습니다. 히스토그램이 뾰족할 수록 정밀도가 높다고 분석할 수 있습니다. **(steepness)**

히스토그램을 MATLAB에서 구현하는 방법과 함수에 대한 옵션은 다음과 같습니다.

![](https://i.ibb.co/jD7n9tF/image.jpg)

hist()함수를 이용하면 (histogram()이 권장되긴 합니다.)
히스토그램 막대의 개수를 지정할 수도 있고, 히스토그램의 각 막대에 대한 counts와 centers도 받아올 수 있습니다.

또한 Bar를 이용해서 히스토그램을 구현하는 것도 가능한데, 이때는 막대와 막대 사이의 간격이 벌어지게 됩니다. (두 개 함수에 유의미한 차이는 없습니다.)
