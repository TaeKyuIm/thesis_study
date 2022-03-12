# The Concrete Distribution: A CONtinuous Relaxation of disCRETE random variables 
## 주소 : https://arxiv.org/abs/1611.00712

딥러닝은 어떻게 학습을 할까? 가중치 행렬을 구성한 뒤, 계속 Forward-Backward Propagation을 반복하며 가중치를 갱신한다.  
가중치를 갱신한다는 관점에서 보면 변수들에 대해 reparamenterization 되는 걸로 볼 수 있는데, 연속형 변수의 경우 잘 진행이 된다.  
그러나 이산형 변수의 경우는?? 이러한 관점에서 나온 것이 바로 Concrete distribution 이다.  
Discrete한 변수들의 경우 1이거나 0 이거나 이다. 그러나 이러한 사실이 reparamenterization을 어렵게 한다. 이를 해결하기 위해 도입한 것이 바로  
Gumbel-softmax 이다. Gumbel Distribution은 최대 혹은 최소값의 분포를 모델링에 이용할때 사용이 된다. 이러한 사실을 이용하여 discrete한 분포를 continous 하게 바꾸는 데 이용한다.

![concrete1](https://github.com/TaeKyuIm/thesis_study/blob/main/image/concrete1.jpg?raw=true)

보다시피 Discrete 일때는 1, 0으로 구분이 되지만, Concrete 일때는 검은색과 흰색 사이의 색깔로 결과가 표시 된다.
