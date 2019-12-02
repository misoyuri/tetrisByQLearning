# Q-Learning Algorithm을 이용한 Tetris Game.
19-2 HGU 모두의 인공지능

21600004 강석운, 21800416 심일호

![ezgif com-resize(1)](https://user-images.githubusercontent.com/28642496/69956426-4d2cdf80-1543-11ea-8490-13d39d24207b.gif)


# 왜 Tetris Game 인가
2016년도 알파고와 이세돌 기사 대국으로 AI와 강화학습에 대해서 흥미가 있었다. 
이번 19-2 HGU 모두의 인공지능 수업을 통해서 AI에 대해서 배우고, 19-2 HGU SW festival에서 육목 AI 대회를 강화학습으로 준비했다. 
이런 경험들을 통해 강화학습에 대한 주제를 가지고 project를 진행하면 좋겠다는 생각을 했고, 누구나 한번쯤은 해본 'Testris Game'을 주제로 정했다.

# Project 개요
1. Q-Learning 이란?
2. Project 실행을 위한 준비
3. Tensor Board로 Log 비교.

# YouTube Link
https://youtu.be/hCvobtc33bc

본 project를 따라할 때 Youtube 영상을 참고하면 더욱 수월하게 할 수 있습니다.

# Q-Learning 이란?
![11](https://user-images.githubusercontent.com/28642496/69955754-c0355680-1541-11ea-82b7-cb0b2cdde3f7.JPG)

1. Q(s, a) 행렬을 Random value로 초기화한다.
2. 초기 상태 s에서 시작한다.
3. 종료 시점까지 반복한다.
      * 액션 a를 선택하여 실행한다.
      * 액션에 따른 보상 r과 변경된 상태 s'를 확인한다.
      * Q-value를 갱신한다.
      * 현재 상태를 변경한다.


![KakaoTalk_20191202_212910702](https://user-images.githubusercontent.com/28642496/69959928-908b4c00-154b-11ea-9156-f7ac98168c7a.png)

본 게임에서 말하는 보상 
 r = (block이 놓일 때마다 +1점)+(line이 clear될 때마다 +(BOARD너비 * (clear된 line개수))점) 이다.


위의 내용을 보기 편하게 도형으로 표현한 그림은 아래와 같다.
![캡처](https://user-images.githubusercontent.com/28642496/69955757-c0cded00-1541-11ea-9d8b-0b06df8759ca.JPG)


# 본 Project를 위한 Requirments
1. pip
2. tensorflow
3. tensorboard
4. Keras 
5. opencv-python
6. numpy
7. Pillow 
8. tqdm

# Requirments 설치 방법
1. CMD or Power Shell을 실행
2. pip install --upgrade pip
3. pip install  'Requirment Name'

# .ipynb file을 .py로 바꾸는 방법
1. CMD or Power Shell을 실행
2. jupyter nbconvert --to script [file name].ipynb 입력
     run.ipynb, tetris.ipynb, logs.ipynb, dqn_agent.ipynb 총 4번 수행

# 실행방법
1. CMD or Power Shell에서 python run.py를 입력
2. jupyter note북에서 rus.ipynb를 실행
     위 두 방법중 하나를 하면 됩니다.

# 저장된 log data를 TensorBoard를 통해 분석하는 방법
1. CMD or Power Shell을 실행
2. log가 저장되어있는 logs 폴더로 이동 (cd logs)
3. tensorboard --host=0.0.0.0 --logdir=[log 폴더의 local 주소] 입력
4. CMD or Power Shell에서 정상 작동 확인
5. Internet Brower를 이용해 http://localhost:6006 로이동.
6. TensorBoard를 이용하는 방법은 Youtube Link로 확인하시면 됩니다.

# 결과 분석
![graph1](https://user-images.githubusercontent.com/28642496/69959236-fd9de200-1549-11ea-9e8f-e5e5209452cd.jpg)
1. batch size가 같을 때 epoch가 크다면 Max Score가 더 높았다.

![qwwq](https://user-images.githubusercontent.com/28642496/69959765-3ee2c180-154b-11ea-8b0a-75dc74152b37.jpg)
2. epoch가 같을 때 batch size가 작다면 Max Score가 더 높았다.

![graph](https://user-images.githubusercontent.com/28642496/69959240-fe367880-1549-11ea-801b-375347d54256.JPG)
3. 전반적으로 batch size가 작고 epoch가 크다면 Max Score가 더 높았다

# 결론
한정적인 episode(반복 횟수) 내에서 Max Score를 가장 크게 하고 싶다면 batch size를 작게하고 epoch를 크게 설정하면 된다.
하지만 batch size가 크고 epoch가 적당한 model에 비해서 안정성이 떨어지기 때문에 score의 차이가 심하다.
