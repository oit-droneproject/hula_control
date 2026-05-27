
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
