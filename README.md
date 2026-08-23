<div align="center">

# 🏆 HSLegendArriver（胜率63.8的炉石传说脚本）

### 帮你走完上传说的路

**读取炉石日志 + 获取炉石盒子打法建议 + 自动执行操作**

**33 分钟：钻石 2 → 传说**  
**一下午：冲到传说约 6000 名**  
**多盘实测胜率：机械骑 82.4%（17 局 14 胜）、号角骑 65%、弃牌术 63.8%**

<br>

> 🔥 已实测支持：**机械骑 / 号角骑 / 弃牌术 / 海盗瞎**  
> 🤖 自动识别对局、读取推荐打法并完成出牌操作

</div>

---

## ✨ 项目简介

**HSLegendArriver（传说到达者）** 是一个用于《炉石传说》的自动化打法执行器。

项目通过读取炉石对局日志，并结合 **炉石盒子「推荐打法」** 提供的推荐操作，自动识别当前对局状态并执行对应的鼠标点击与键盘操作。


简单来说：

> **炉石盒子负责告诉你“怎么打”，HSLegendArriver 负责帮你“打出去”。**

目前已经使用多套卡组进行了实际天梯测试。

## 📊 实测卡组胜率

| 卡组 | 胜率 | 实测场次 |
|---|---|---|
| 机械骑 | 82.4% | 17 局 14 胜 |
| 号角骑 | 65% | 未统计 |
| 弃牌术 | 63.8% | 多盘实测 |
| 海盗瞎 | 已实测支持 | — |

## 🖥️ 实时日志浮窗（右上角）

自动对局开始时，屏幕**右上角**会出现一个**置顶半透明**小窗，实时滚动显示自动化日志，方便你在游戏里直观看到每一步：

- **自己回合开始**那一行（`[SYS] 回合 N 开始：延时` / `轮到己方操作`）用**绿色**高亮；
- `[推荐]` / `[执行]` → 白，`等待` → 灰；
- 右侧带**滚动条**，可向上翻看历史（刷新日志时不会再被拉回最底）；
- **按住鼠标左键拖动**可把窗口挪到任意位置；
- 随「开始对战」自动弹出，对局结束随 `web_ui` 退出。

> 提示：若炉石是**全屏独占**模式，Windows 桌面悬浮窗会被游戏盖住而看不到；把炉石设为**窗口化 / 无边框**即可让浮窗显示在游戏画面上。

## 🎯 校准截图区域（适配你本机盒子 UI 大小）

盒子「推荐打法」面板的位置/大小会随**盒子窗口大小、分辨率**不同而变化，程序默认的截图区域不一定刚好对准面板。首次使用或换了盒子窗口大小后，用画框工具手动校准一次：

### 1. 打开校准工具
- 网页控制台点「**校准推荐区域**」按钮；或命令行运行 `python calibrate_roi.py`。

### 2. 屏幕上出现绿框
- 屏幕上的**绿框** = 程序实际截图范围；
- 右下角有一个**缩放手柄**。

### 3. 拖动对齐
- 拖**右下角手柄** → 调整大小；
- 按住绿框**区域（不含右下角手柄）**拖动 → 整体移动；
- 把盒子面板顶部的 **「打法参考A」红头区域**框进绿框（程序靠识别这个标题判断面板是否在框内）。

### 4. 保存 / 退出
- 按 **S** 保存（写入 `ui_config.json`）；
- 按 **Esc** 退出。

### 5. 重开对局生效
- 保存后**重开一局**，程序会读取新的推荐区域再开始识别。

> 提示：本工具**无实时 OCR 预览窗**（为流畅做了精简），对齐后由自动化实际识别验证；程序固定 **1920×1080、缩放 100%**，如需更大/更小的盒子窗口，重新画框即可。

## 🃏 已测试卡组

### 号角骑（针对脏牧特攻）

```text
# 职业：圣骑士
# 模式：狂野模式
# 
AAEBAaToAgaD3gO2igS8jwbOnAbRqQblwQcMiA740gKR5APJoAThpATBxAXI+AWFjgaZjgb1lQaDwgea/AcAAA==
# 
# 想要使用这副套牌，请先复制到剪贴板，然后在游戏中点击“新套牌”进行粘贴。
```

### 机械骑

```text
# 职业：圣骑士
# 模式：狂野模式
# 
AAEBAaToAgiftwPM6wP5pAS5/gXHpAaf4Qa/+Qad3QcLpfUCh64DkrUE1L0E2tMEhKUF2dAF4vEGupYH2uIHmvwHAAEE1/4Cnd0H87MGx6QG9rMGx6QG6N4Gx6QGAAA=
# 
# 想要使用这副套牌，请先复制到剪贴板，然后在游戏中点击“新套牌”进行粘贴。
```
### ✅ 弃牌术

目前测试最充分的卡组之一。

卡组代码：

```text
AAEBAa35AwaPggPV0QP5xgXxoQb2oQbGsgcMzge1uQPQ4QOYkgWrkgWVygbXlweEmQekrQfWvgfZvgfPvwcAAA==
```

### ✅ 海盗瞎

已完成实际对局测试，个人认为可以正常执行打法。

---

## 🐍 详细安装（含 pip 与清华镜像，适合新手，老手建议虚拟环境）

> 需要 **Python 3.12**（自带 pip）。以下从零说明如何安装 Python、装 pip，并快速装好本项目依赖。

### 1. 安装 Python 3.12
- 到 <https://www.python.org/downloads/> 下载 **Python 3.12** 安装包；
- 安装时**务必勾选 “Add python.exe to PATH”**；
- 装完在 PowerShell 运行 `python --version`，看到版本号即成功（新版 Python 自带 pip）。

### 2. 如果没有 pip
一般新版 Python 自带 pip；若提示没有 pip，先下载安装：
- 下载 `get-pip.py`：浏览器打开 <https://bootstrap.pypa.io/get-pip.py> 另存，或在 PowerShell 运行：
  ```text
  curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
  ```
- 在 `get-pip.py` 所在目录运行：
  ```text
  python get-pip.py
  ```
- 验证：`python -m pip --version`

### 3. 用清华 TUNA 镜像安装依赖
- 在项目根目录（含 `requirements.txt` 的位置）打开 PowerShell，运行：
  ```text
  pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
  ```
- 依赖较大（含 PaddleOCR / PaddlePaddle），耐心等待下载安装完成。

### 4. 启动
- **以管理员身份**运行：
  ```text
  python web_ui.py
  ```
- 浏览器会自动打开 `http://127.0.0.1:8765`（若被占用会自动换端口，以控制台打印为准）。


---



## 🚀 快速开始

只需要 **3 步**。

### 1️⃣ 打开炉石与炉石盒子

启动：

- 《炉石传说》
- 《炉石传说盒子》



在卡组列表中选择需要运行的卡组，例如：

**弃牌术**

![炉石盒子「推荐打法」界面选择弃牌术](docs/step1-box.png)

---

### 2️⃣ 修改配置

> 💡 嫌麻烦？可以跳过本节，直接使用 **Web 控制台**在页面上填写配置（见下文「🖥️ Web 控制台」）。

打开：

```text
constants/constants.py
```

找到以下配置：

```python
HEARTHSTONE_LOG_ROOT = "D:/Hearthstone/Logs"

YOUR_NAME = "YOURID"
```

修改为自己的信息。

#### `HEARTHSTONE_LOG_ROOT`

炉石日志目录。

例如：

```python
HEARTHSTONE_LOG_ROOT = "D:/Hearthstone/Logs"
```

通常可以在炉石传说安装目录中找到：

```text
Logs
```

文件夹。

#### `YOUR_NAME`

填写你的完整炉石 BattleTag：

```python
YOUR_NAME = "用户名#编号"
```

例如：

```python
YOUR_NAME = "为所欲为、异灵术#54321"
```

---

### 3️⃣ 管理员权限启动 ⚠️

> **这一步非常重要。**

因为程序需要模拟鼠标点击和键盘操作，所以必须使用 **管理员权限** 运行。

#### Windows

右键：

```text
命令提示符
```

选择：

> **以管理员身份运行**

进入项目目录：

```bash
cd /d D:\HSLegendArriver
```

安装依赖：

```bash
pip install -r requirements.txt
```


启动：

```bash
pip install -r requirements.txt   # 首次运行需要安装依赖
python web_ui.py
```

浏览器会自动打开：

```text
http://127.0.0.1:8765
```

### 游戏界面
![游戏界面](docs/game.png)

## 🤝 Contributing

如果你在使用过程中遇到问题，或者有功能建议，**欢迎直接提交 Issue**。

建议在 Issue 中尽量提供：

- 🐛 **Bug 反馈以及游戏界面运行截图**：说明问题现象、复现步骤和运行环境附上运行截图
- 💡 **功能建议**：描述希望支持的功能或使用场景
- 🃏 **卡组适配**：注明卡组名称、相关交互以及异常情况
- 🖼️ **界面问题**：如涉及点击坐标或 UI 变化，建议附截图


---

## ⭐

如果这个项目：

- 让你觉得有意思
- 给了你一些自动化 / 炉石 AI 的灵感

欢迎点一个 **Star ⭐**，这对我真的很重要！！！

你的 Star 会让我知道还有人在使用这个项目，也会成为继续适配新版本和新卡组的动力。

> **如果真的靠它上传说了，回来留个 Star 吧 😎**

---

## 🙏 致谢

本项目参考了以下开源项目：

- [Yiyuan-Dong/AutoHS](https://github.com/Yiyuan-Dong/AutoHS)
- [FallAbyss/AutoHS](https://github.com/FallAbyss/AutoHS)

感谢原作者们提供的思路和开源代码。

---

## ⚠️ Disclaimer

本项目仅用于 **技术研究与代码交流**。



---

<div align="center">

### 🏆 HSLegendArriver

**让 AI 帮你走完最后一段上传说的路。**

如果你觉得这个项目有意思：

## ⭐ Star 一下吧 ⭐

</div>
