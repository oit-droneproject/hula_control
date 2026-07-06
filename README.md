
## 離陸と着陸

### tello_sample01.py
以下のコードはhulaを離陸させて、着陸させるコードである。
#### single_fly_takeoff()
離陸するメソッド
#### single_fly_touchdown()
着陸するメソッド
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

## 前進、停止、後進
### tello_sample02.py
以下のコードはhulaを前進、停止、後進させるメソッドである。

#### single_fly_forward(x)
$0< x < 300$

xはcm

hulaをxcm前進させる。

#### single_fly_hover_flight(x)

xは秒数

hulaをx秒停止させる。

#### single_fly_back()
$0< x < 300$

xはcm

hulaをxcm前進させる。

```python
import pyhula
api = pyhula.UserApi()
if not api.connect():
  print("connect error")
else:
  print('connection to station by wifi')
api.single_fly_takeoff()

api.single_fly_forward(50)
api.single_fly_hover_flight(1)
api.single_fly_back(50)

api.single_fly_touchdown()
```

## 上昇と下降
### tello_sample03.py

#### single_fly_up(x)

xはcm

hulaをxcm上昇させるメソッド。

#### single_fly_down(x)

xはcm

hulaをxcm下降させるメソッド。

```python
import pyhula
api = pyhula.UserApi()
if not api.connect():
  print("connect error")
else:
  print('connection to station by wifi')

api.single_fly_up(50)
api.single_fly_hover_flight(1)
api.single_fly_down(50)

api.single_fly_takeoff()
```


## 前後左右

### tello_sample04.py

#### single_fly_left(x)

$0<x<300$

hulaをxcm左に並行移動させるメソッド。

#### single_fly_right(x)

$0<x<300$

hulaをxcm右に並行移動させるメソッド。

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

