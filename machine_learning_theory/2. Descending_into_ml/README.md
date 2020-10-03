# Descengind into ML : Linear Regression

**오랫동안 귀뚜라미는 시원한 날보다 더운날 더 자주 우는 것으로 알려져 왔습니다.**  
전문가 곤충 학자들이 수십년에 걸쳐 1분당 귀뚜라미가 우는 횟수와 온도에 관한 데이터를 목록으로 작성했습니다. 이 두 특성관계를 학습시켜 보는 데이터베이스틑 받았다고 해 봅시다. 올바른 첫 번째 단계는 데이터를 그래프로 만들어 검토하는 것 입니다.

<div style="text-align:center;">
<img width="400px" src="https://user-images.githubusercontent.com/48028667/93706313-ed4e0680-fb5f-11ea-94aa-d07d6a695250.PNG">
</div>

위의 그래프를 통해 우는 횟수가 증가할 수록 온도가 올라가는 것을 확인할 수 있습니다. 그렇다면 우는 횟수와 온도는 선형관계일까요? 맞습니다. 아래의 그림을 통해 확인할 수 있습니다.

<br />


<div style="text-align:center;">
<img width="400px" src="https://user-images.githubusercontent.com/48028667/93706315-f048f700-fb5f-11ea-82fc-bba6ea1de44a.PNG">
</div>

위 그림의 선에 데이터들이 정확하게 통과하지는 않지만 선을 통해서 데이터의 관계를 명확하게 보여 줍니다. 대수학을 적용하면 다음과 같이 작성할 수 있습니다.

<br />

<div style="text-align:center;">
    <span style="font-weight:bold;">y = mx + b</span>
</div>

여기서,

- **y**는 섭씨온도, 즉 예측하려는 값입니다.
- **m**은 선의 기울기 입니다.
- **x**는 1분당 우는 횟수, 즉 입력 feature 값입니다.
- **b**는 y 절편 입니다.

며신러닝의 관습에 따라 모델의 방적식은 약간 다르게 작성하게 됩니다.

<div style="text-align:center;">
    <span style="font-weight:bold;">y' = b + w1x1</span>
</div>

여기서,

- **y'** 는 예측된 Label(얻고자 하는 출력)입니다.
- **b** 는 y 절편 입니다. 일부 머신러닝 자료에서는 w0 라고도 합니다.
- **w1**은 Feature1의 가중치 입니다. 가중치는 위에서 m으로 표현된 '기울기'와 같은 개념입니다.
- **x1**은 Feature(알려진 입력) 입니다.

새로운 분당 우는 횟수 x1에서 온도 y'를 추론(예측)하려면 x1값을 이 모델에 삽입하기만 하면 됩니다. 좀 더 정교한 모델을 원한다면 많은 Feature를 사용할 수 있습니다. 아래는 세 가지 특성에 의존하는 모델을 나타냅니다.

<div style="text-align:center;">
    <span style="font-weight:bold;">y' = b + w1x1 + w2x2 + w3x3</span>
</div>

<br /><br /><br />


# Descending into ML : Traning and Loss

Model을 학습시킨다는 것은 단순히 말하면 Label이 있는 데이터로 부터 올바른 가중치를 이용해 편향값을 결정한다는 것 입니다. 지도 학습에서 머신러닝 알고리즘은 다양한 예를 검토하고 손실을 최소화 하는 모델을 찾아 만들어 내는데 이 과정을 **경험적 위험 최소화(Empirical risk minimization)** 이라 부릅니다.

**손실(Loss)** 는 잘못된 예측에 대한 패널티 입니다. 즉 손실은 얼마나 예측이 잘못되었는지 수치로서 나타내 줍니다. 모델의 예측이 완벽하다면 손실은 0이고, 잘못되었을 수록 그 수치는 커집니다. 모델 학습의 목표는 모든 예에서 평균적으로 작은 손실을 갖도록 하는 것 입니다.  
아래의 그림을 보겠습니다.
<div style="text-align:center;">
<img src="https://user-images.githubusercontent.com/48028667/93708280-e7f8b800-fb6f-11ea-885c-ed754de4061d.PNG">
</div>
- 화살표는 손실을 나타냅니다
- 파란선은 예측을 나타냅니다.
- 왼쪽은 손실이 큰 모델이고, 오른쪽은 손실이 작은 모델 입니다.


<br /><br />

### Squared loss : a popular loss function
선형 회귀 모델에서 제곱 손실(**L2**)라고 불리는 손실 함수를 살펴 보겠습니다. 데이터 하나의 제곱 손실은 다음과 같이 나타 냅니다.
```text
= the square of the difference between the label and the prediction
= (observation - prediction(x))^2
= (y - y')^2
```
**평균 제곱 오차(Mean Square Error)** 는 예시당 평균 제곱 손실 입니다. MSE를 계산하려면 개별 예의 모든 제곱 손실을 합한 다음 예의 수로 나눠야 합니다.
<div style="text-align:center;">
<img src="https://user-images.githubusercontent.com/48028667/93708283-ea5b1200-fb6f-11ea-9b9e-4af34450a48c.PNG">
</div>

여기서,
- (x, y)는 예(Example)이며, 다음과 같습니다.
    - x는 Model이 예측하는데 사용하는 Feature 집합(ex:온도, 나이, 성공률)
    - y는 Example의 Label(ex:분당 우는 소리) 입니다.
- prediction(x)은 특성 집합 x와 결합된 가중치 및 편향의 함수 입니다.
- D는 (x, y) 쌍과 같이 여러 Label이 있는 Example이 포함된 Data set 입니다.
- N은 D에 포함된 Example의 수 입니다.

<br />

**MSE**는 머신러닝에서 흔히 사용되지만, 모든 상황에서 최선인 유일한 손실 함수는 아닙니다.

