# Hula-jp 運動制御用 API

pyhula ライブラリを使って、ドローン「hula」を制御するための API リファレンスです。各サンプルコードは、共通して次の手順で動作します。

1. `pyhula.UserApi()` で API オブジェクトを生成する
2. `api.connect()` で Wi-Fi 経由でステーションに接続する
3. 各種メソッドを呼び出して機体を制御する

---

## 共通の接続処理

すべてのサンプルコードは、以下の接続処理から始まります。

```python
import pyhula

api = pyhula.UserApi()

if not api.connect():
    print("connect error")
else:
    print("connection to station by wifi")
```

`api.get_battery()` を使うと、飛行前にバッテリー残量を確認できます。

---

##  離陸と着陸

| メソッド | 説明 |
| --- | --- |
| `single_fly_takeoff()` | 機体を離陸させる |
| `single_fly_touchdown()` | 機体を着陸させる |

**tello_sample01.py**

```python
import pyhula

api = pyhula.UserApi()
if not api.connect():
    print("connect error")
else:
    print("connection to station by wifi")

api.single_fly_takeoff()
api.single_fly_touchdown()
```

---

##  前進・停止・後進

| メソッド | 引数 | 説明 |
| --- | --- | --- |
| `single_fly_forward(x)` | `0 < x < 300`（cm） | 機体を x cm 前進させる |
| `single_fly_back(x)` | `0 < x < 300`（cm） | 機体を x cm 後進させる |
| `single_fly_hover_flight(x)` | `x`（秒） | 機体を x 秒間その場で停止（ホバリング）させる |

**tello_sample02.py**

```python
import pyhula

api = pyhula.UserApi()
if not api.connect():
    print("connect error")
else:
    print("connection to station by wifi")

print(f"battery={api.get_battery()}")

api.single_fly_takeoff()
api.single_fly_forward(50)
api.single_fly_hover_flight(1)
api.single_fly_back(50)
api.single_fly_touchdown()
```

---

##  上昇と下降

| メソッド | 引数 | 説明 |
| --- | --- | --- |
| `single_fly_up(x)` | `x`（cm） | 機体を x cm 上昇させる |
| `single_fly_down(x)` | `x`（cm） | 機体を x cm 下降させる |

**tello_sample03.py**

```python
import pyhula

api = pyhula.UserApi()
if not api.connect():
    print("connect error")
else:
    print("connection to station by wifi")

print(f"battery={api.get_battery()}")

api.single_fly_takeoff()
api.single_fly_up(50)
api.single_fly_hover_flight(1)
api.single_fly_down(50)
api.single_fly_touchdown()
```

---

##  前後左右への移動

前進・後進に加えて、左右への並行移動を組み合わせられます。

| メソッド | 引数 | 説明 |
| --- | --- | --- |
| `single_fly_left(x)` | `0 < x < 300`（cm） | 機体を x cm 左へ並行移動させる |
| `single_fly_right(x)` | `0 < x < 300`（cm） | 機体を x cm 右へ並行移動させる |

**tello_sample04.py**

```python
import pyhula

api = pyhula.UserApi()
if not api.connect():
    print("connect error")
else:
    print("connection to station by wifi")

print(f"battery={api.get_battery()}")

api.single_fly_takeoff()
api.single_fly_left(50)
api.single_fly_hover_flight(1)
api.single_fly_right(50)
api.single_fly_forward(50)
api.single_fly_hover_flight(1)
api.single_fly_back(50)
api.single_fly_touchdown()
```

---

##  旋回

| メソッド | 引数 | 説明 |
| --- | --- | --- |
| `single_fly_turnleft(x)` | `x`（度） | 機体を x 度、左（反時計回り）に回転させる |
| `single_fly_turnright(x)` | `x`（度） | 機体を x 度、右（時計回り）に回転させる |

**tello_sample05.py**

```python
import pyhula

api = pyhula.UserApi()
if not api.connect():
    print("connect error")
else:
    print("connection to station by wifi")

print(f"battery={api.get_battery()}")

api.single_fly_takeoff()
api.single_fly_turnleft(90)
api.single_fly_hover_flight(1)
api.single_fly_turnright(90)
api.single_fly_touchdown()
```

---

## 再離陸

離陸と着陸を繰り返す例です。`time.sleep(x)` で、次の離陸までに x 秒間の待機を挟みます。

**tello_sample06.py**

```python
import pyhula
import time

api = pyhula.UserApi()
if not api.connect():
    print("connect error")
else:
    print("connection to station by wifi")

api.single_fly_takeoff()
api.single_fly_touchdown()
time.sleep(10)  # 10秒間スリープ

api.single_fly_takeoff()
api.single_fly_touchdown()
time.sleep(10)  # 10秒間スリープ

api.single_fly_takeoff()
api.single_fly_touchdown()
```


| 上下移動 | `single_fly_up(x)` / `single_fly_down(x)` | `x`（cm） |
| 旋回 | `single_fly_turnleft(x)` / `single_fly_turnright(x)` | `x`（度） |
| 停止 | `single_fly_hover_flight(x)` | `x`（秒） |
