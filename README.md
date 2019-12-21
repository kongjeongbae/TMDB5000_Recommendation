# 상품 추천 알고리즘



- 파이썬 환경 설정 : Python 3.6.8 가상환경 생성 (Surprise 패키지 설치를 위해)

  

- 추천 알고리즘에 대한 개념

  
  1. 콘텐츠 기반 필터링(Content based filtering)
     
  2. 협업 필터링(Collaborative filtering) 
  
     2.1 최근접 이웃(Nearest Neighbor) 협업 필터링
  
     ​	2.1.1 사용자 기반(User-User)
  
     ​	2.1.2 아이템 기반(Item-Item)
  
     2.2 잠재 요인(Latent Factor) 필터링



- 확률적 경사 하강법을 이용한 행렬 분해

    1. 확률적 경사 하강법(Stochastic Gradient Descent, SGD) 

        1.1 경사 하강법 (Gradient Descent, **GD)**

        1.2 확률적 경사 하강법(Stochastic Gradient Descent, SGD)
        
        
        
    2. 확률적 경사 하강법(SGD)을 이용한 행렬 분해
       
    3. SGD를 이용한 행렬 분해의 절차 



- 장르 속성을 이용한 영화 컨텐츠 기반 필터링 실습

  1. 장르 컨텐츠 유사도 측정
     
  2. 장르 컨텐츠 필터링을 이용한 영화추천



- 아이템 기반 최근접 이웃 협업 필터링 실습

  1. 데이터 가공 및 변환

  2. 영화간 유사도 산출

  3. 아이템 기반 최근접 이웃 협업 필터링으로 개인화된 영화 추천
      <img src="https://render.githubusercontent.com/render/math?math=\hat{R}_{u,i} = \displaystyle\sum_{}^{N} (S_{i,N} * R_{u,N}) / \displaystyle\sum_{}^{N} ( |S_{i,N}| )">
     $$\hat{R}_{u,i} = \displaystyle\sum_{}^{N} (S_{i,N} * R_{u,N}) / \displaystyle\sum_{}^{N} ( |S_{i,N}| )$$
     
     - $\hat{R}_{u,i}$: 사용자 u, 아이템 i의 개인화된 예측 평점 값
      - ${S}_{i,N}$: 아이템 i와 가장 유사도가 높은 Top-N 개 아이템의 유사도 벡터
      - ${R}_{u,N}$: 사용자 u의 아이템 i와 가장 유사도가 높은 Top-N개 아이템에 대한 실제 평점 벡터



- ```python
  def matrix_factorization(R, K, steps=200, learning_rate = 0.01, r_lambda = 0.01)
  ```

- ```pyth
  P, Q = matrix_factorization(ratings_matrix.values, K=50, steps=200, learning_rate=0.01, r_lambda=0.01)
  
  pred_matrix = np.dot(P, Q.T)
  
  ratings_pred_matrix = pd.DataFrame(data=pred_matrix, index=ratings_matrix.index, columns=ratings_matrix.columns)
  ratings_pred_matrix.head(3)
  ```
