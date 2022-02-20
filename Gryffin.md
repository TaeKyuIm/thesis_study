# Gryffin: An algorithm for Bayesian optimization of categorical variables informed by expert knowledge
## 주소 : https://arxiv.org/abs/2003.12127

햄버거가 무엇일까? 보통은 빵 사이에 패티를 넣는 것을 생각한다. 그러나 '패티 2장에 중간에 빵을 넣는 것이 어떻게 보면 더 맛있지 않을까??'  
라는 생각이 들 수도 있다. 또한 현대사회는 귀찮음의 사회다. "햄버거에서 최적의 소스조합을 인공지능이 알아서 찾아줄 수 있지 않을까?" 라는 생각이 들 수도 있다.  
이러한 질문들을 제조업에 적용한 것이 바로 Gryffin Algorithm이라고 생각을 한다.  

최근 인공지능이 도입이 되면서 로제타폴드, 알파폴드 등 단백질 구조를 예측을 하는 모델들이 발표되고 있다.  
인공지능으로 Material Discovery 분야가 점점 더 커지고 있다. 처음에 ML, DL을 배울때 Regression, Classification으로 어떻게 다른  
물성치를 찾을 수 있을까, 생각이 많이 들었다. 그러나 나는 문제에 대해 접근을 잘못 하고 있었다.  

결국은 Material Discovery라는 것이 수학적으로는 특정 상황에서 해를 찾는 과정으로 생각할 수 있고, 바로 산업공학에서의 최적화 문제로 접근을 하여야 한다.  

최적화 문제의 경우 그냥 바로 답을 찾는 것이 아니라, 특정 하나 또는 여러 Objective Function들을 정의를 하고, 이러한 함수들에 대해 Optimization 즉 우리가 고등학교때 했던, 정의역이 주어졌을때 함수를 미분해서, Optimal Point를 찾고, 양 끝 점들의 값을 확인하여 값의 크기가 제일 크거나 작은 값을 찾는 과정을 진행하여야 한다.  

결국은 Objective Function의 값을 크게 하거나, 낮게 하는 작업을 취하여야 하는데, 이러한 작업에서 등장하는 것이 바로 Genetic Algorithm 이다.  
유전알고리즘의 이름에도 알 수 있듯이, Objective Function을 설정해주면, 이진법 형태로 인코딩된 값들을 이용하여 Crossover, Mutation, Selection을 반복하여 최적의 해를 찾는다.

이제 논문을 읽을 준비는 끝났다.  

논문을 보면 신소재공학에서 변수는 사실 Categorical 변수라고 나와있다. 이게 뭔 소린가 싶었는데, 유전 알고리즘에 대해 읽고, 이진법 인코딩을 읽으면 이해가 된다. 예를 들어 20~40에서 최적화 과정을 진행하고 싶을때, l = 5로 설정하면, 20을 [0 0 0 0 0], 40을 [1 1 1 1 1]로 인코딩 하는 함수를 만들 수 있다.  

이러한 과정이 왜 필요할까? 물리학이나 화학에서 특정 성분이 1mg 넣었다고 하면, 정말로 1mg이 들어갔다고 확정 지을 수 있는가, 아니라고 생각을 한다. 따라서 어느정도 discrete한 접근이 필요하다고 생각을 하고, 그것에 대한 답이 GA와 이진법 형태의 인코딩이라 생각을 한다.

##
이제 알고리즘의 작동원리를 보면 앞서 말한대로 정의역의 범위를 정한 뒤 인코딩 해준다. 그리고 논문 중간에

"categorical input spaces are mapped onto continuous ones with variational autoencoders and using large datasets"라고 나와있다.

즉 내가 정의역을 어느정도 이진법 형태로 바꿔주고, 변분인코더를 통해 연속적인 값으로 mapping 해준다.  

이 문구가 gryffin 알고리즘의 핵심이라 생각을 하는데, 변분인코더를 통해 latent 변수에 대해 확률분포가 학습이 되고, 이러한 학습된 분포를 통해 바로 최적화를 진행을 하는 것이라 이해를 했다....!

결국 kernel density를 approximate를 통해 특정 값들이 주어졌을때, 이를 생성모델을 통해 정확한 함수형태를 찾는 다는 것이고, 함수형태가 결정이 되면 바로 Optimal Point가 존재하는 구간을 찾아낼 수 있을 것이다.

따라서 이진법 형태의 인코딩을 하면 simplex 형태로 정의역의 범위가 설정이 될 것이고, V.A.E를 통해 확률분포가 학습이 되어, 특정 값에 대한 분포가 그려질 것이다.  

즉 Generative + Optimization = Gryffin 이라고 생각을 할 수 있다.
