# 🐍 Python 套件管理教學文件 | Python Package Management Guide

> 本教學介紹如何管理 Python 套件（含 pip、conda、poetry 等），  
> 並附上中英對照說明與實用指令表。  

---

## 📚 一、什麼是套件管理？ | What Is Package Management?

**套件管理（Package Management）** 是指安裝、更新、移除與維護第三方模組（libraries）的過程。  
Python 的標準庫功能雖強，但許多應用仍需額外安裝外部套件。

---

## ⚙️ 二、主要套件管理工具比較 | Comparison of Package Managers

| 工具 | 英文名稱 | 特點 | 優點 | 適用場景 |
|------|-----------|------|------|----------|
| **pip** | Python Installer for Packages | Python 內建工具 | 官方支援、使用簡單 | 一般使用者 |
| **conda** | Anaconda Package Manager | 可管理多語言環境 | 支援 Python 以外語言 | 資料科學、AI |
| **poetry** | Modern Python Packaging | 自動管理依賴與虛擬環境 | 現代專案管理 | 軟體開發者 |
| **pipenv** | pip + virtualenv 整合 | 自動產生 lock file | 環境可重現性佳 | 部署與專案管理 |
| **uv / hatch** | New-gen Python Tool | 高速、PEP 621 支援 | 現代化開發 | 進階開發者 |

---

## 💡 三、pip 基本操作 | Basic pip Commands

| 操作 | 中文說明 | 指令範例 |
|------|-----------|-----------|
| 安裝套件 | Install a package | `pip install numpy` |
| 安裝特定版本 | Install specific version | `pip install pandas==2.2.1` |
| 更新套件 | Upgrade package | `pip install --upgrade scikit-learn` |
| 移除套件 | Uninstall package | `pip uninstall matplotlib` |
| 查詢套件 | List installed packages | `pip list` |
| 匯出套件列表 | Export all packages | `pip freeze > requirements.txt` |
| 根據列表安裝 | Install from requirements | `pip install -r requirements.txt` |

---

## 🧱 四、虛擬環境管理 | Virtual Environment Management

### 為什麼要使用虛擬環境？
不同專案可能需要不同版本的套件，虛擬環境可避免版本衝突。

### 建立虛擬環境
```bash
python -m venv myenv
```

### 啟動虛擬環境
- Windows：
  ```bash
  myenv\Scripts\activate
  ```
- macOS / Linux：
  ```bash
  source myenv/bin/activate
  ```

### 退出環境
```bash
deactivate
```

---

## 🧩 五、使用 conda 管理環境與套件 | Managing with Conda

| 操作 | 中文說明 | 指令 |
|------|-----------|------|
| 建立新環境 | Create new environment | `conda create -n myenv python=3.10` |
| 啟動環境 | Activate environment | `conda activate myenv` |
| 安裝套件 | Install packages | `conda install numpy pandas matplotlib` |
| 匯出設定 | Export environment | `conda env export > environment.yml` |
| 從設定重建 | Rebuild environment | `conda env create -f environment.yml` |

---

## 🚀 六、使用 Poetry 管理專案 | Managing Projects with Poetry

| 操作 | 中文說明 | 指令 |
|------|-----------|------|
| 初始化專案 | Initialize project | `poetry init` |
| 安裝套件 | Add dependency | `poetry add requests` |
| 啟動虛擬環境 | Activate environment | `poetry shell` |
| 鎖定依賴 | Install + lock dependencies | `poetry install` |

---

## 📦 七、套件發佈流程 | Publishing Your Own Package

1. 建立 `setup.py`
2. 打包套件：
   ```bash
   python setup.py sdist bdist_wheel
   ```
3. 安裝上傳工具：
   ```bash
   pip install twine
   ```
4. 上傳到 PyPI：
   ```bash
   twine upload dist/*
   ```

---

## 🔍 八、常見問題與解法 | Common Issues & Fixes

| 問題 | 解決方式 |
|------|-----------|
| pip 無法使用或版本太舊 | `python -m ensurepip --upgrade` |
| 加快下載速度（使用鏡像） | `pip install -i https://pypi.tuna.tsinghua.edu.cn/simple 包名` |
| conda 下載慢 | 設定清華或中科大鏡像源 |
| 套件相依性衝突 | 使用 `pip check` 或改用 `poetry` |

---

## 🧠 九、實務建議 | Practical Recommendations

- ✅ 每個專案應建立獨立虛擬環境  
- 📄 使用 `requirements.txt` 或 `poetry.lock` 確保重現性  
- 🧰 大型專案建議使用 **Poetry / Conda**  
- 💻 小型腳本可用 **pip + venv**  
- 🚀 若要發佈套件，建議使用 **twine + PyPI**  

---

## 📚 延伸閱讀 | Further Reading

- 官方文件：[https://pip.pypa.io](https://pip.pypa.io)
- Anaconda：[https://docs.conda.io](https://docs.conda.io)
- Poetry：[https://python-poetry.org](https://python-poetry.org)
- Python Packaging Authority：[https://packaging.python.org](https://packaging.python.org)

---

© 2025 Python 教學文件 — 由 ChatGPT 整理製作

