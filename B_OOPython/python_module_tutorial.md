# 🐍 Python 模組教學文件 (Python Module 教學全指南)

> 作者：T Ben  
> 版本：v1.0  
> 檔案編碼：UTF-8  
> 適用對象：初學者～進階開發者  
> 內容：什麼是模組？如何匯入？如何安裝？如何自己寫？常用模組示範與測驗題庫

---

## 📖 目錄
1. 什麼是模組與套件 (Module vs Package)
2. 匯入模組的方法 (import 語法)
3. 標準函式庫 vs 第三方模組
4. 虛擬環境 (venv)
5. 使用 pip 安裝模組
6. 常用內建模組教學
7. 常見第三方模組教學
8. 自訂模組範例
9. 常見 import 錯誤
10. 測驗題庫 (選擇題)

---

## 🧩 一、什麼是模組與套件

| 名稱 | 說明 | 範例 |
|------|------|------|
| 模組 (Module) | 一個 `.py` 檔案 | `math.py`, `mytool.py` |
| 套件 (Package) | 一個包含 `__init__.py` 的資料夾 | `numpy`, `pandas` |
| 標準函式庫 | Python 內建模組 | `os`, `json`, `math` |
| 第三方模組 | 額外安裝模組 | `requests`, `matplotlib` |

---

## 🧭 二、匯入模組的方法

```python
# 1️⃣ 整包匯入
import math
print(math.sqrt(16))

# 2️⃣ 匯入特定函式
from math import sqrt, pi
print(sqrt(9), pi)

# 3️⃣ 重新命名
import numpy as np

# 4️⃣ 匯入全部（不建議）
from math import *
```

---

## ⚙️ 三、標準函式庫 vs 第三方模組

| 類型 | 是否需安裝 | 範例 |
|------|-------------|------|
| 標準函式庫 | ❌ 不需 | `os`, `math`, `json` |
| 第三方模組 | ✅ 需 `pip install` | `requests`, `numpy` |

---

## 💻 四、虛擬環境 (venv)

```bash
# 建立虛擬環境
python -m venv venv

# 啟動虛擬環境
# Windows
venv\Scripts\activate
# macOS/Linux
source venv/bin/activate
```

優點：
- 專案獨立環境，避免版本衝突
- 常見於企業部署與教學開發

---

## 📦 五、使用 pip 安裝模組

```bash
pip install requests numpy pandas
pip list
pip freeze > requirements.txt
pip install -r requirements.txt
```

---

## 🧮 六、常用內建模組教學

### 1. math
```python
import math
print(math.pi)
print(math.sqrt(25))
```

### 2. random
```python
import random
print(random.randint(1, 10))
print(random.choice(['A','B','C']))
```

### 3. datetime
```python
from datetime import datetime
print(datetime.now())
```

### 4. os / pathlib
```python
import os
from pathlib import Path
print(os.getcwd())
Path('data').mkdir(exist_ok=True)
```

---

## 🌐 七、常見第三方模組教學

### 1. requests
```python
import requests
r = requests.get('https://api.github.com')
print(r.status_code)
```

### 2. numpy
```python
import numpy as np
a = np.array([1, 2, 3])
print(a.mean())
```

### 3. pandas
```python
import pandas as pd
df = pd.DataFrame({'x':[1,2,3], 'y':[4,5,6]})
print(df.describe())
```

### 4. matplotlib
```python
import matplotlib.pyplot as plt
plt.plot([1,2,3],[4,5,6])
plt.show()
```

---

## ✏️ 八、自訂模組範例

### mymath.py
```python
def add(a,b):
    return a+b
```

### main.py
```python
import mymath
print(mymath.add(3,4))
```

---

## 🪲 九、常見 import 錯誤

| 錯誤訊息 | 原因 | 解決方式 |
|-----------|------|-----------|
| ModuleNotFoundError | 模組未安裝 | `pip install` |
| ImportError | 模組結構錯誤 | 檢查模組層級 |
| 同名衝突 | 本地檔案與標準模組重名 | 改檔名 |

---

## 🧪 十、測驗題庫（選擇題，含答案）

### 🧩 單選題
1️⃣ `import math` 後要呼叫平方根函式，應使用：  
A. `sqrt(9)`  B. `math.sqrt(9)`  C. `math->sqrt(9)`  D. `import.sqrt(9)`  
✅ **答案：B**

2️⃣ `from math import pi` 的作用是什麼？  
A. 匯入整個 math 模組  B. 匯入變數 pi  C. 匯入所有函式  D. 刪除 pi  
✅ **答案：B**

3️⃣ 哪個模組可用來隨機選取清單中的元素？  
A. `random`  B. `math`  C. `os`  D. `time`  
✅ **答案：A**

4️⃣ 若想操作系統檔案與資料夾應使用哪個模組？  
A. `os`  B. `sys`  C. `string`  D. `datetime`  
✅ **答案：A**

5️⃣ 下面哪個屬於第三方模組？  
A. `os`  B. `json`  C. `requests`  D. `math`  
✅ **答案：C**

6️⃣ `pip install numpy` 的用途是？  
A. 啟動 Python  B. 安裝套件  C. 建立虛擬環境  D. 移除模組  
✅ **答案：B**

7️⃣ `python -m venv venv` 的功能是？  
A. 安裝虛擬套件  B. 建立虛擬環境  C. 刪除環境  D. 查看版本  
✅ **答案：B**

8️⃣ 下列何者不是合法的 import？  
A. `import math`  B. `from math import sqrt`  C. `import math.sqrt`  D. `from math import pi`  
✅ **答案：C**

9️⃣ 若要畫圖，常用哪個模組？  
A. `pandas`  B. `matplotlib`  C. `re`  D. `os`  
✅ **答案：B**

🔟 匯出所有套件列表的指令是？  
A. `pip list > packages.txt`  B. `pip freeze > requirements.txt`  C. `pip export all`  D. `pip --save`  
✅ **答案：B**

---

📘 **結語**
Python 的模組系統是其最大優勢之一。學會使用模組，可以讓開發更快、更穩、更乾淨。
