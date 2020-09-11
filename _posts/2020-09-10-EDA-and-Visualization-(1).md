---
title: EDA and Visualization (1)
tag: R데이터분석
---

탐색적데이터분석과 R프로그래밍에서는 R을 사용합니다.
기본적인 연산자 등의 개념은 이미 숙지하고 있다고 간주하기에, 초반에는 많은 내용을 생략할 것입니다. 주로 **일반적인 프로그래밍 언어(C++등)와 R의 차이점**을 중심으로 설명할 예정입니다.

# 변수
R은 인터프리트 언어기 때문에, 사용법은 MATLAB과 상당히 유사합니다. 다만 R 특유의 변수 사용법이 몇 가지 있습니다.

* **변수에 값 할당시 <- 사용 권장** : 변수에 값을 할당하는 것을 a <- 3과 같이 표현합니다. 이렇게 표현하는 이유는 a = 3으로 표현했을 때 파라미터로 인식될 가능성이 있기 때문입니다.
* **자료형을 크게 구분짓지 않음** : integer, double이 물론 존재합니다만, 이를 통칭해 numeric이라고 자주 사용하며 정수로 선언하더라도 기본값은 double입니다.

# 데이터와 객체
R은 객체 지향 프로그래밍 언어입니다. 연산되는 모든 값은 객체라고 보아도 무방한데, 객체에서도 여러 가지 종류가 나뉩니다.

* **데이터 종류** : 숫자(numeric), 문자(character), 진리값(logical), NA, NULL
* **객체 종류** : 벡터(vector), 팩터(factor), 행렬(matrix), 배열(array), 데이터 프레임(data frame), 리스트(list)

R에서 숫자는 integer, double, complex가 있습니다. **integer와 double을 합쳐 numeric이라고 합니다.**

# NA, NaN, NULL
NA는 **Not Available**의 약자로, 값이 존재하지 않는 경우를 논리(logical)값으로 나타냅니다.
NaN은 **Not a Number**의 약자로, 수학에서 정의되지 않는 값을 의미합니다. (0/0등)
NULL은 NA와 비슷하게 값이 존재하지 않는 경우를 의미하지만, 논리값이 아니며 값 자체가 없습니다.

# R에서 새로 다루는 객체
벡터(Vector)는 c() (combine)함수로 생성할 수 있으며, **각 원소에 대응되는 이름을 지정해줄 수 있습니다.**

```
> x <- c(bmc = 420, kjs = 30509)
> x
bmc kjs
420 30509
> names(x)
"bmc" "kjs"
```

팩터(Factor)는 R에서 사용하는 독득한 데이터 종류입니다. **범주형**데이터를 다루는데 주로 사용합니다. 기본적으로는 문자와 동일하지만 이 문자에는 레벨(level)이 존재합니다.
값을 일단 숫자로 나타내고, 그 숫자에 대응되는 문자를 따로 저장하기 때문에 메모리 관리에 용이합니다. factor() 함수로 생성합니다.

```
> i = c("a","b","c")
> x = factor(i, levels = c("a","b","c","d"))
> x
[1] a b c
Levels: a b c d
```

행렬(Matrix)은 말 그대로 행과 열을 가진 구조이며, MATLAB에서의 사용법과 유사합니다. 벡터와 마찬가지로 **원소가 한 가지의 데이터 종류만을 가질 수 있습니다.** matrix() 함수로 생성합니다.
matrix( data : 행렬로 생성할 벡터, nrow : 행의 수, ncol : 열의 수, byrow : 벡터를 행렬로 만들 때 어느 방향으로 데이터를 채울지. TRUE인 경우 행우선, FALSE인 경우 열우선(기본))
nrow나 ncol을 입력하지 않아도 만들 수 있으며(열벡터)  **하나만 입력해도 행렬을 만들 수 있습니다.**
또한 벡터에서 원소에 이름을 부여하듯이, 행렬에서도 rownames()와 colnames()함수로 행과 열 각각 이름을 부여할 수 있습니다.

```
> x = matrix(data = 1:4, nrow = 2, ncol = 2)
> x
     [,1] [,2]
[1,]    1    3
[2,]    2    4
> x = matrix(data = 1:4, nrow = 2, ncol = 2, byrow = TRUE)
> x
     [,1] [,2]
[1,]    1    2
[2,]    3    4
```

배열(Array)은 구조를 가진 객체입니다. 행렬을 포함하고 있고, 차원의 개념이 등장합니다.
배열 역시도 한 가지의 데이터 종류로만 이루어질 수 있습니다.
배열은 array() 함수와 벡터를 이용해 생성합니다.

배열 생성의 예를 들면 dim 인자에 c(3, 2)를 입력하면 3행 2열인 행렬이 생성됩니다. c(3, 2, 2)를 입력하면 3x2x2 배열이 생성됩니다. 쉽게 말하면 3행 2열인 행렬이 2개 (3x2x2 차원의 구조) 생성됨.

```
> x <- array(data = 1:8, dim = rep(2,3))
> x
, , 1

     [,1] [,2]
[1,]    1    3
[2,]    2    4

, , 2

     [,1] [,2]
[1,]    5    7
[2,]    6    8
```