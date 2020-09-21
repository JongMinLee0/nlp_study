# Reducing Loss : An Iterative Approach

머신러닝이 반복을 통해 어떻게 손실을 줄이는지 알아 보겠습니다.  
반복학습은 숨겨진 물건을 찾는 [Hot and Cold](https://www.howcast.com/videos/258352-how-to-play-hot-and-cold) 놀이와 비슷 합니다. 이 놀이에서 **숨겨진 물건**이 최적 모델이 됩니다. 처음 임의의 지점에서 시작해서(w1의 값은 0) 시스템이 손실 값을 알려줄때까지 기다립니다. 그런 다음 다른 값을 추정해서(w1의 값은 0.5) 손실 값을 확인 합니다. 사실 이 방식은 제대로만 하면 점점 가까워지게 되어 있습니다. 진짜 중요한 것은 최적의 모델을 가능한 효율적으로 찾는 것 입니다.  
다음은 머신러닝 알고리즘이 모델을 학습하는데 사용하는 반복적인 시행착오 과정을 보여줍니다.

<p align="center">
<img src="https://user-images.githubusercontent.com/48028667/93763634-c1f51580-fc4c-11ea-807e-403176316d71.PNG" style="width: 600px">
</p>

<br />

반복 전략은 주로 대규모 데이터 세트에 적용하기 용이하여 머신러닝 전반에서 널리 사용되고 있습니다. 이 모델은 하나 이상의 특성(feature)을 입력하여 하나의 예측(y')을 출력합니다.  
이해를 위해 하나의 특성을 가지고 하나의 예측을 반환하는 모델을 생각해 보겠습니다.

<br />

<p align="center">
y' = b + w1x1
</p>

<br />

b와 w1의 초기값을 무엇으로 설정해야 할까요?  
선형 회귀 문제에서 초기값은 별로 중요하지 않습니다. 임의의 값을 정해도 되지만 일단 다음 값을 사용해 보겠습니다.

- b = 0
- w1 = 0

최초 특성 값이 10이라고 가정하겠습니다. 이 특성 값을 예측 함수(prediction function)에 입력하면 다음과 같이 출력 됩니다.

- y' = 0 + 0(10)
- y' = 0

위의 다이어 그램에서 '손실 계산' 과정은 이 모델에서 사용한 [손실 함수](https://github.com/JongMinLee0/nlp_study/tree/master/machine_learning_theory/Descending_into_ml) 입니다. 손실 함수는 두개의 입력 값을 취합니다.

- y' : 특성 x에 대한 모델의 예측 값 입니다.
- y : 특성 x에 대한 올바른 라벨 입니다.

다이어그램은 이제 '매개변수 업데이트 계산' 과정에 도달합니다. 이 지점에서 머신러닝 시스템은 손실 함수의 값을 검토하여 **b**와 **w1**의 새로운 값을 생성 합니다. 이 값을 이용하여 다시 값을 출력하고 손실값이 가장 낮은 모델 매개 변수를 발견할 때까지 반복 학습합니다. 전체 손실이 변하지 않거나 매우 느리게 변할때 모델이 **수렴(converged)** 했다고 합니다.