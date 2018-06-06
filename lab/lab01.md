## 모두를 위한 딥러닝 Lab#01
#### 2018.06.07

---

- Tensorflow	
	- 데이터 플로우 그래프
		- 그래프에서 **Node**는 숫자 연산(Operation)을 의미한다.
		- 엣지는 다차원 데이터 어레이(Tensor)를 의미한다.
	- Install
		> 겁나 오래 걸린다...

		```
		>> pip install --upgrade tensorflow
		```
		
	- Version Check

		```
		>>> import tensorflow as tf
		>>> tf.__version__
		'1.8.0'
		>>>
		``` 	 
		
	- Hello Tensorflow
		
		```
		# constant 생성
		# 하나의 Node 생성됨
		>>> hello = tf.constant("Hello, Tensorflow!")
		
		# 그래프를 실행하려면 세션을 만들어야됨..(?)
		>>> sess = tf.Session()
		
		# 세션 실행 후 출력
		>>> print(session.run(hello))
		b'Hello, Tensorflow!'
		>>>
		```
	
	- Computational Graph

		> ```3``` 노드와 ```4``` 노드를 더하는 그래프.
		
		- 노드 생성 

			> Graph Build

			```
			>>> node1 = tf.constant(3.0, tf.float32)
			>>> node2 = tf.constant(4.0, tf.float32)
			>>> node3 = tf.add(node1, node2)
			```
			
		- 노드 출력 

			```
			>>> print("node1: ", node1, " node2: ", node2)
			node1:  Tensor("Const_1:0", shape=(), dtype=float32)  node2:  Tensor("Const_2:0", shape=(), dtype=float32)	
			>>> print("node3: ", node3)
			node3:  Tensor("Add:0", shape=(), dtype=float32)
			>>>
			```
			
		- 실행 및 출력 

			> feed data and run graph, update variables in the graph and return value
		
			```
			>>> sess = tf.Session()
			>>> print("sess.run(node1, node2): ", sess.run([node1, node2]))
			sess.run(node1, node2):  [3.0, 4.0]
			>>> print("sess.run(node3): ", sess.run(node3))
			sess.run(node3):  7.0
			>>>
			```
			
		- 작동 순서
			1. 텐서플로 오퍼레이션을 통한 그래프 빌드
			2. sess.run()을 통해 그래프를 실행
			3. 그 결과로 그래프 데이터 업데이트 혹은 리턴
		
	- Placholder
		
		> 그래프를 실행시키는 단계에서 그래프를 미리 만들어놓고, 나중에 실제 데이터로 변경할 때 사용
		
		```
		>>> a = tf.placeholder(tf.float32)
		>>> b = tf.placeholder(tf.float32)
		>>> adder_node = a + b
		
		>>> print(sess.run(adder_node, feed_dict={a: 3, b: 4.5}))
		7.5
		
		>>> print(sess.run(adder_node, feed_dict={a: [1,3], b: [2,4]}))
		[3. 7.]
		>>> 
		```
	
		- 작동 순서
			1. 텐서플로 오퍼레이션을 통한 그래프 빌드(plaholder로 노드 생성)
			2. sess.run()을 통해 그래프를 실행, feed_dict로 많은 데이터 전달
			3. 그 결과로 그래프 데이터 업데이트 혹은 리턴

	- Tensors

		- Ranks

			> 몇 차원 이냐?
			
			|Rank|Math entity| Python example|
			---|---|---
			0|Scalar| s = 483
			1|Vector| v = [1.1, 2.2, 3.3]
			2|Matrix| m = [[1,2,3], [4,5,6], [7,8,9]]
			3|3-Tensor| t = [[[2],[4],[6]],[[8],[10],[12]],[[14],[16],[18]]]
			n|n-Tensor| ...
		
		- Shapes
			
			> 각 **Element**에 몇 개 씩 들어있나?
			
			|Rank|Shape|Dimension number|Python example|
			---|---|---|---
			0|[]|0-D| A Scalar
			1|[D0]|1-D| [5]
			2|[D0, D1]|2-D| [3, 4]
			3|[D0, D1, D3]|3-D| [1, 4, 3]
			n|[D0, D1, ... , Dn-1]|n-D| [D0, D1, ... , Dn-1]
			
			```
			# [3 3) or [3, 3]
			t = [[1,2,3], [4,5,6], [7,8,9]]
			```
			
		- Types

			> 데이터의 타입
			
			|Data type|Python type|Description|
			---|---|---
			**DT_FLOAT**|**tf.float32**|**32비트 floating point**
			DT_DOUBLE|tf.float64|64비트 floating point
			DT_INT8|tf.int8|8비트 singned integer
			DT_INT16|tf.int16|16비트 singned integer
			**DT_INT32**|**tf.int32**|**32비트 singned integer**
			DT_INT64|tf.int64|64비트 singned integer
			...|...|...
			
			
			