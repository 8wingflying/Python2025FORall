# 🐍 Python 內建模組完整教學文件（中英對照版）

> 作者：T Ben  
> 檔案編碼：UTF-8  
> 版本：v1.1  
> 說明：本文件為 Python 內建標準模組（Standard Library）教學的進階版，包含模組用途、範例與進階補充。此版本新增：ZIP 封裝、PDF 匯出說明，以及附錄命令教學。

---

## 📦 一、打包與匯出教學（Packaging & Export）

### 🔹 將此文件打包成 ZIP 檔
使用 Python 的 `shutil` 模組可直接壓縮整個教學文件：
```python
import shutil
shutil.make_archive('Python_Builtin_Modules', 'zip', '.')
```
執行後會產生 `Python_Builtin_Modules.zip` 檔案。

### 🔹 匯出為 PDF 教學文件
可使用 `pandoc` 或 `markdown-pdf` 套件：
```bash
# 方法一：使用 pandoc
pandoc Python_內建模組教學文件.md -o Python_內建模組教學文件.pdf

# 方法二：使用 markdown-pdf（Node.js）
npm install -g markdown-pdf
markdown-pdf Python_內建模組教學文件.md
```

---

## 🧮 數學與隨機 Math & Random Modules

| 模組名稱 | 英文說明 | 中文功能摘要 |
|-----------|------------|----------------|
| `math` | Mathematical functions | 提供基本數學運算與常數（sin、sqrt、pi） |
| `cmath` | Complex math | 處理複數運算 |
| `decimal` | Fixed-point and floating decimal arithmetic | 高精度小數運算 |
| `fractions` | Rational numbers | 分數表示與計算 |
| `random` | Generate pseudo-random numbers | 隨機數與隨機選取 |
| `statistics` | Mathematical statistics functions | 平均數、變異數、中位數等統計函式 |

**範例：**
```python
import math, random, statistics
print(math.sqrt(16))      # 4.0
print(random.choice([1, 2, 3]))  # 隨機選擇
print(statistics.mean([1, 2, 3]))  # 2
```

---

## 🕒 日期與時間 Date & Time

| 模組名稱 | 英文說明 | 中文功能摘要 |
|-----------|------------|----------------|
| `datetime` | Basic date and time types | 日期與時間物件操作 |
| `time` | Time access and conversions | 時間戳記、延遲 |
| `calendar` | General calendar-related functions | 年曆、閏年判斷 |

**範例：**
```python
from datetime import datetime
import time, calendar
print(datetime.now())  
print(time.time())  
print(calendar.isleap(2024))  # True
```

---

## 💾 檔案與目錄 Files & Directories

| 模組 | 功能 |
|------|------|
| `os`, `os.path` | 檔案系統操作、環境變數 |
| `shutil` | 高階檔案操作（複製、刪除） |
| `pathlib` | 物件導向路徑操作 |
| `glob` | 檔案通配符搜尋 |

**範例：**
```python
from pathlib import Path
import os, shutil
print(os.getcwd())
shutil.copy('a.txt', 'backup.txt')
p = Path('data')
print(p.exists())
```

---

## 🌐 網路與通訊 Network & Communication

| 模組 | 功能 |
|------|------|
| `socket` | 低階網路通訊 |
| `urllib` | 網頁請求與下載 |
| `http` | HTTP 協定支援 |
| `ftplib` | FTP 檔案傳輸 |

**範例：**
```python
from urllib import request
html = request.urlopen('https://www.python.org').read()
print(len(html))
```

---

## ⚙️ 系統與環境 System & Environment

| 模組 | 功能 |
|------|------|
| `sys` | 系統參數與命令列 |
| `platform` | 系統平台資訊 |
| `subprocess` | 執行外部命令 |
| `argparse` | 命令列參數解析 |

**範例：**
```python
import sys, subprocess
print(sys.version)
subprocess.run(['echo', 'Hello Python!'])
```

---

## 🧠 資料結構 Data Structures

| 模組 | 功能 |
|------|------|
| `collections` | 高階資料結構（deque、Counter） |
| `heapq` | 最小堆排序 |
| `bisect` | 二分搜尋與插入 |
| `enum` | 列舉類型（Enum） |

**範例：**
```python
from collections import Counter
import heapq
print(Counter('banana'))
nums = [3, 1, 2]
heapq.heapify(nums)
print(heapq.heappop(nums))  # 1
```

---

## 🔒 安全與加密 Security & Cryptography

| 模組 | 功能 |
|------|------|
| `hashlib` | 雜湊演算法（MD5, SHA256） |
| `hmac` | 密鑰雜湊驗證 |
| `secrets` | 安全隨機數 |
| `ssl` | SSL/TLS 支援 |

**範例：**
```python
import hashlib, secrets
h = hashlib.sha256(b'hello').hexdigest()
print(h)
print(secrets.token_hex(16))
```

---

## 🧰 測試與除錯 Testing & Debugging

| 模組 | 功能 |
|------|------|
| `unittest` | 單元測試框架 |
| `doctest` | 文件測試 |
| `logging` | 紀錄日誌 |
| `traceback` | 錯誤堆疊追蹤 |

**範例：**
```python
import logging
logging.basicConfig(level=logging.INFO)
logging.info('This is a log message.')
```

---

## 🔀 並行與非同步 Concurrency & Async

| 模組 | 功能 |
|------|------|
| `threading` | 多執行緒處理 |
| `multiprocessing` | 多程序處理 |
| `asyncio` | 非同步 I/O |
| `queue` | 執行緒安全佇列 |

**範例：**
```python
import asyncio
async def hello():
    print('Hello Async!')
asyncio.run(hello())
```

---

## 📘 附錄：查看所有內建模組 Appendix

### 🔍 查看所有模組
```python
help('modules')
```

### 🧩 僅顯示內建模組
```python
import sys
print(sys.builtin_module_names)
```

---

© 2025 | 教學作者：T Ben | License: CC BY-NC-SA 4.0

