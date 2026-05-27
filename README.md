
## 離陸と着陸
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

