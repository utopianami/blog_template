---
title: Predicting Win In Champion Selection
updated: 2019-12-21
---

###  롤 챔피언 선택만으로 승패 예측

[롤 챔피언 선택 화면 이미지 추가]



#### 1. 과정

- 데이터 수집
- 모델 학습
- 결과 분석



#### 2. 데이터 수집

- API key 발급: [link](https://developer.riotgames.com/)
  
- 한국 서버 기준, 랭커 유저 리스트 만들기
  
  ```python
  import requests
  api_key = 'api_key'
  
  tiers = ['CHALLENGER', 'GRANDMASTER', 'MASTER']
  rank_api = 'https://kr.api.riotgames.com/lol/league-exp/v4/entries/RANKED_SOLO_5x5'
  
  rankers = []
  for tier in tiers:
      page = 1
      while(True):
          request_url = f'{rank_api}/{tier}/I?page={page}&api_key={api_key}'
          user_infos = requests.get(request_url).json()
          
          if len(user_infos) == 0:
              break
          
          rankers += user_infos
          page += 1
  ```
  
- 라이엇 API를 이용해 위에서 수집한 유저들의 게임  n개 모으기
  
  -  k를 조절하면서 n을 늘림
  
- Train/validation/Test로 나눔



#### 3. 모델 학습

- 어떤 모델을 사용할지 ??????



#### 4. 결과 분석

- 정확도 
- Visualization
  - 챔프 t-sne 



#### 5. Appendix

- API  발급
- 