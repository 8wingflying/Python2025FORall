# ⚡ uv 教學文件 | uv Python Package Manager Guide

> **uv** 是一個由 [Astral](https://astral.sh) 開發的現代化 Python 套件與虛擬環境管理器，  
> 以 Rust 編寫、速度極快、完全相容於 `pip`、`virtualenv`、`poetry` 與 PEP 621。  
>  
> 它結合了 **pip + virtualenv + pip-tools + poetry** 的功能，是未來 Python 套件管理的新主流。
> 
> https://docs.astral.sh/uv/getting-started/
> https://www.youtube.com/watch?v=aVXs8lb7i9U

---

## 🧩 一、uv 是什麼？ | What is uv?

**uv** 是一個「一體化」的 Python 工具，用於：
- 📦 管理套件與依賴（如 pip）
- 🌱 建立與管理虛擬環境（如 venv）
- 🧰 管理專案與建置（如 poetry）
- 🚀 超高速下載與安裝（比 pip 快 8–10 倍）

---

## ⚙️ 二、安裝 uv | Installation

### 1️⃣ 使用 curl 安裝
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

### 2️⃣ 使用 pip 安裝（可行但不建議）
```bash
pip install uv
```

### 3️⃣ 驗證安裝
```bash
uv --version
```

---

## windows平台安裝
```
PS> powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

## 🧱 三、基本指令 | Basic Commands

| 指令 | 功能 | 範例 |
|------|------|------|
| `uv pip install <套件>` | 安裝套件（比 pip 快） | `uv pip install numpy` |
| `uv pip list` | 查看已安裝套件 | `uv pip list` |
| `uv pip freeze` | 匯出 requirements.txt | `uv pip freeze > requirements.txt` |
| `uv pip uninstall <套件>` | 移除套件 | `uv pip uninstall pandas` |
| `uv python list` | 顯示已安裝 Python 版本 | `uv python list` |
| `uv python install 3.12` | 安裝特定 Python 版本 | `uv python install 3.12` |
| `uv run` | 在虛擬環境中執行程式 | `uv run python app.py` |

---

## 🧰 四、虛擬環境管理 | Managing Virtual Environments

| 操作 | 指令 |
|------|------|
| 建立新環境 | `uv venv` |
| 指定 Python 版本建立環境 | `uv venv --python 3.11` |
| 啟動環境 | Linux/macOS：`source .venv/bin/activate`<br>Windows：`.venv\Scripts\activate` |
| 列出所有環境 | `uv venv list` |
| 移除環境 | `uv venv remove <name>` |

---

```
uv venv # 用 .venv 資料夾建立虛擬環境
uv venv --python 3.11 # 指定 Python 版本
uv pip install ruff # 在虛擬環境安裝套件
source .venv/bin/activate # 啟用虛擬環境
# .venv\Scripts\activate # Windows
deactivate # 退出虛擬環境
```

## 🧪 五、專案初始化與開發流程 | Project Workflow

1️⃣ **初始化新專案**
```bash
uv init myproject
cd myproject
```

2️⃣ **新增套件**
```bash
uv add requests numpy
```

3️⃣ **建立 lock file（確保重現性）**
```bash
uv lock
```

4️⃣ **執行專案**
```bash
uv run python main.py
```

5️⃣ **移除依賴**
```bash
uv remove requests
```

---

## 🧩 六、uv 與其他工具對照表 | uv vs pip vs poetry

| 功能 | uv | pip | poetry |
|------|----|-----|---------|
| 安裝速度 | 🚀 極快（Rust 實作） | 慢 | 中等 |
| 相依性解析 | ✅ 自動解決 | ❌ 手動處理 | ✅ 自動 |
| 環境管理 | ✅ 內建 | ❌ 需 virtualenv | ✅ 內建 |
| lock file | ✅ 支援 | ❌ 無 | ✅ 有 |
| 專案初始化 | ✅ `uv init` | ❌ 無 | ✅ `poetry init` |
| 相容性 | ✅ pip、PEP 621 | ✅ 廣泛 | ✅ PEP 621 |
| 適用對象 | 開發者、資料科學 | 初學者 | 專案管理 |

---

## ⚡ 七、uv 的優勢 | Advantages of uv

- 🚀 **速度超快**：由 Rust 撰寫，比 pip 快數倍  
- 🔒 **確保可重現性**：自動產生 lock 檔案  
- 🔄 **全相容 pip/venv**：可無縫切換專案  
- 📦 **支援多版本 Python 管理**  
- 🧱 **整合建構、打包、執行於同一工具中**  

---

## 🧠 八、實務建議 | Best Practices

- 在每個專案根目錄使用 `uv init` 初始化  
- 將 `.venv` 加入 `.gitignore`  
- 使用 `uv lock` 固定依賴版本  
- 建議取代 `pip` 作為預設安裝工具  
- 可整合至 CI/CD Pipeline（速度快、重現性佳）  

---

## 📚 九、參考資源 | References

- 官方網站：[https://docs.astral.sh/uv](https://docs.astral.sh/uv)  
- GitHub Repo：[https://github.com/astral-sh/uv](https://github.com/astral-sh/uv)  
- 相關專案：[https://astral.sh](https://astral.sh)

---

© 2025 uv Python 教學文件 — 由 ChatGPT 整理製作

