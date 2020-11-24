# 손실 함수 (cost function)
손실 함수란 신경망이 학습할 수 있도록 해주는 지표이다. 모델의 출력값과 사용자가 원하는 출력값의 차이, 즉 오차를 말한다.

이 손실 함수 값이 최소화되도록 하는 가중치와 편향을 찾는 것이 바로 학습이다. 일반적인 손실 함수로 평균 제곱 오차(MSE)나 교차 엔트로피 오차(CEE)를 사용한다.

## 손실함수를 사용하는 이유
신경망 학습에서 최적의 매개변수를 탐색할 때 손실함수의 값을 가능한 한 작게 하는 매개변수 값을 찾는다.

이때, 매개변수의 미분(기울기)을 계산하고, 그 미분 값을 토대로 매개변수 값을 갱신하는 과정을 반복한다.

손실 함수와는 달리 정확도는 매개변수의 변화에 둔감하고, 또한 변화가 있다하여도 불연속적으로 변화하기 때문에 미분을 할 수 없다.

미분이 되지 않으면 최적화를 할 수 없으므로 정확도가 아닌 손실 함수를 지표로 삼아 학습을 해나가는 것이다.


## 평균 제곱 오차(Mean Squared Error : MSE)
<img width="175" alt="6-1" src="https://user-images.githubusercontent.com/63298243/92325346-b74f5380-f084-11ea-86b8-e78de707e8f6.png">

계산이 간편하여 가장 많이 사용되는 손실 함수이다.

기본적으로 모델의 출력 값과 사용자가 원하는 출력 값 사이의 거리 차이를 오차로 사용한다.

그러나 오차를 계산할 때 단순히 거리 차이를 합산하여 평균내게 되면, 거리가 음수로 나왔을 때 합산된 오차가 실제 오차보다 줄어드는 경우가 생긴다.

그렇기 때문에 각 거리 차이를 제곱하여 합산한 후에 평균내는 것이다.

위의 식에서는 1/2를 곱하는 것으로 되어 있으나 실제로는 2가 아닌 전체 데이터의 수를 나누어 1/n을 곱해주어야 한다.

 - 거리 차이를 제곱하면 좋은 점은, 거리 차이가 작은 데이터와 큰 데이터 오차의 차이가 더욱 커진다는 점이다. 이렇게 되면 어느 부분에서 오차가 두드러지는지 확실히 알 수 있다는 장점이 있다.

## 교차 엔트로피 오차(Cross Entropy Error : CEE)
<img width="169" alt="6-2" src="https://user-images.githubusercontent.com/63298243/92325348-b8808080-f084-11ea-9036-036fade6c6eb.png">

기본적으로 분류(Classification) 문제에서 원-핫 인코딩(one-hot encoding)했을 경우에만 사용할 수 있는 오차 계산법이다.

위의 식에서 t값이 원-핫 인코딩된 벡터이고, 거기에다 모델의 출력 값에 자연로그를 취한 것이 곱해지는 형태이다.

결과적으로 교차 엔트로피 오차는 정답일 때의 모델 값에 자연로그를 계산하는 식이 된다.