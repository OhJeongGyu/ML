## 모두를 위한 딥러닝 Lec#01
#### 2018.06.07

---

- 머신러닝 기본
	- 머신러닝이란 무엇인가?
		- 기존 소프트웨어의 한계
			
			> explicit programming? 일반적인 프로그램. 스팸 필터링, 자동 운전 -> 규칙과 데이터가 너무 많아 한계가 있음

		- 머신러닝?

			> 컴퓨터에게 무엇인가 배울 수 있도록(스스로 학습) 능력을 주는 것.
			
	- 학습의 종류
		- Supervised Learning

			> 라벨링 되어 있는 데이터 (고양이나 강아지 사진에 라벨링을 붙이고 이에 따라 분류)
			- 이미지 라벨링
			- 이메일 스팸 필터링
			- 시험 점수 예측
			
		- Unsupervised Learning

			> 라벨이 없는 데이터 (구글 뉴스 그루핑, 월드 클러스터링)
	
	- Training Data Set
		1. 트레이닝 데이터 셋(X -> 인풋, Y -> 인풋에 대한 정답 or 라벨?)을 학습시켜 **Model**을 만든다
		1. 새로운 데이터(X)을 모델 입력하면 이에 대한 정답, 라벨을 얻을 수 있음

	- Types of supervised learning
		- 시험 공부 시간에 따른 시험 성적 예측
		
			> Regression (시간 범위가 연속적임)
			
		- 시험 공부 시간에 따른 P/NP

			> Binary Classification (두 개로 분류가 가능하다)
			
		- 시험 공부 시간에 따른 등급 예측 (A,B,C,D,F)
			- Multi-label Classification (여러 개로 분류가 가능하다)

	- 시험 점수 예측
		- Regression
			- 트레이닝 데이터 셋
			
				|x(hours) | y(score)|
				|---|---|
				|10|90|
				|9|80|
				|3|50|
				|2|30|
			- x = 7 ? y = 75 라고 예측.
		- Binary Classification
			- 트레이닝 데이터 셋
			
				|x(hours) | y(pass/fail)|
				|---|---|
				|10|P|
				|9|P|
				|3|F|
				|2|F|
			- x = 7 ? F/P 예측.
		- Multiple Classification
			- 트레이닝 데이터 셋
			
				|x(hours) | y(grade)|
				|---|---|
				|10|90|
				|9|80|
				|3|50|
				|2|30|
			- x = 7 ? grade 예측.

	



