
## 離陸と着陸
#### single_fly_takeoff()
離陸するメソッド
#### single_fly_touchdown()
着陸するメソッド
### tello_sample01.py
```python
import pyhula
api = pyhula.UserApi()
if not api.connect():
  print("connect error")
else:
  print('connection to station by wifi')
api.single_fly_takeoff()
api.single_fly_touchdown()
```

## 前進、停止、更新
### tello_sample02.py
```python
import pyhula
api = pyhula.UserApi()
if not api.connect():
  print("connect error")
else:
  print('connection to station by wifi')
api.single_fly_takeoff()

api.single_fly_forward(100)
api.single_fly_hover_flight(10)
api.single_fly_back(100)

api.single_fly_touchdown()
```

## 上昇と下降
### tello_sample03.py
```python
import pyhula
api = pyhula.UserApi()
if not api.connect():
  print("connect error")
else:
  print('connection to station by wifi')

api.single_fly_up(50)
api.single_fly_hover_flight(10)
api.single_fly_down(50)

api.single_fly_takeoff()
```


## 前後左右
### tello_sample04.py
```python
import pyhula
api = pyhula.UserApi()
if not api.connect():
  print("connect error")
else:
  print('connection to station by wifi')

api.single_fly_takeoff()

api.single_fly_left(100)
api.single_fly_hover_flight(10)
api.single_fly_right(100)

api.single_fly_forward(100)
api.single_fly_hover_flight(10)
api.single_fly_back(100)

api.single_fly_touchdown()
```

## 旋回
### tello_sample05.py
```python
import pyhula
api = pyhula.UserApi()
if not api.connect():
  print("connect error")
else:
  print('connection to station by wifi')

api.single_fly_takeoff()

single_fly_turnleft(angle,led)
api.single_fly_hover_flight(10)
single_fly_turn(angle,led)

api.single_fly_forward(100)
api.single_fly_hover_flight(10)
api.single_fly_back(100)

api.single_fly_touchdown()
```

