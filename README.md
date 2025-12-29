# Python Flask 局域网文件分享工具

一个基于 Python Flask 的个人文件服务器，提供现代化的网页界面用于在局域网内分享和管理文件。

## 🌟 特性

- 现代化、响应式的网页界面
- 支持文件上传、下载、预览和删除
- 支持批量操作（批量下载、批量删除）
- 全局文件搜索功能
- 支持设置访问密码保护
- 支持文件夹浏览和导航
- 支持文本文件在线预览
- 支持图片文件在线预览
- 完全离线运行，无需外网连接

## 📋 系统要求

- Windows 7 或更高版本
- Python 3.6 或更高版本

## 🚀 快速开始

### 1. 克隆项目

```bash
git clone <repository-url>
cd Python-Flask-Share
```

### 2. 创建虚拟环境

```bash
python -m venv venv
```

### 3. 激活虚拟环境

```bash
# Windows CMD
venv\Scripts\activate

# Windows PowerShell
venv\Scripts\Activate.ps1
```

### 4. 安装依赖

在线安装：
```bash
pip install flask Flask-Dropzone
```

离线安装（推荐）：
```bash
# 项目已包含所有必需的wheel文件，直接安装
pip install --find-links wheels --no-index flask Flask-Dropzone
```

### 5. 启动服务

双击运行 `启动器.bat` 文件，按照交互式菜单提示进行操作：

1. 选择运行模式（前台运行/后台运行）
2. 设置共享目录（默认为程序目录下的 shared 文件夹）
3. 设置端口号（默认为 5000）
4. 设置访问密码（可选）

启动成功后，可以在浏览器中访问 `http://localhost:5000`（或你设置的其他端口）来使用文件服务器。

## 📁 项目结构

```
Python-Flask-Share/
│
├── 启动器.bat                  <-- 唯一的启动入口
├── server.py                   <-- 核心后端应用
├── requirements.txt            <-- 依赖包列表
├── wheels/                     <-- 离线安装包 (包含所有依赖的wheel文件)
├── templates/                  <-- 存放所有 HTML 页面
│   ├── index.html
│   ├── login.html
│   └── search_results.html
├── static/                     <-- 存放所有静态资源 (CSS/JS/图标)
│   ├── css/
│   │   ├── dropzone.min.css
│   │   └── fancybox.css
│   └── js/
│       ├── dropzone.min.js
│       ├── fancybox.umd.js
│       └── feather.min.js
└── venv/                       <-- Python 虚拟环境 (需要自己创建)
```

### **⚙️ 个性化与自定义指南**

您可以轻松修改以下变量来定制您的服务器，无需深入代码。

| 功能            | 所在文件          | 如何修改                                                                  | 描述                                                                                                             |
| :-------------- | :---------------- | :------------------------------------------------------------------------ | :--------------------------------------------------------------------------------------------------------------- |
| **默认共享目录**  | `启动器.bat`      | 修改 `set "SHARE_FOLDER_DEFAULT=..."` 的值为您的路径，如 `D:\Downloads`。 | 启动器在不输入任何内容时，默认使用的共享文件夹路径。                                                               |
| **默认端口**      | `启动器.bat`      | 修改 `set "PORT_DEFAULT=5000"` 的值为您想要的端口，如 `8888`。                | 服务器运行时监听的网络端口。                                                                                     |
| **默认密码**      | `启动器.bat`      | 修改 `set "PASSWORD_DEFAULT=..."` 的值为您的密码，如 `admin`。留空则默认无密码。 | 启动器在不输入任何内容时，默认设置的访问密码。                                                                   |
| **登录有效期**    | `server.py`       | 修改 `app.permanent_session_lifetime = datetime.timedelta(days=7)` 的天数。 | 用户登录一次后，保持登录状态的时间。                                                                             |
| **会话安全密钥**  | `server.py`       | 修改 `app.secret_key = b'_5#y2L"F4Q8z\n\xec]/'` 为任意复杂的字节字符串。      | 用于加密用户会话信息，更改它可以让旧的登录凭证失效。                                                             |
| **UI 主题颜色**   | `templates/index.html` | 在 `<style>` 标签内，修改 `:root` 中的 `--primary-color` 的值，如 `#ff6347`。 | 控制界面中所有链接、按钮和图标的主要颜色。                                                                       |
| **UI 背景颜色**   | `templates/index.html` | 在 `<style>` 标签内，修改 `:root` 中的 `--background-color` 的值，如 `#ffffff`。 | 控制页面的主要背景色。                                                                                           |
| **UI 文件夹颜色** | `templates/index.html` | 在 `<style>` 标签内，修改 `:root` 中的 `--folder-icon-color` 的值。       | 单独控制文件夹图标的颜色。                                                                                       |
| **UI 文件颜色**   | `templates/index.html` | 在 `<style>` 标签内，修改 `:root` 中的 `--file-icon-color` 的值。         | 单独控制文件图标的颜色。                                                                                         |

---
## 🔗离线静态资源开放地址

这是确保服务器**完全离线**运行的关键。以下文件需放入 `static` 文件夹内（项目内已包含）。
*   **Feather Icons**:
    *   下载地址: `https://unpkg.com/feather-icons`
    *   文件 `dist/feather.min.js` -> 放入: `static/js/feather.min.js`
*   **FancyBox**:
    *   下载地址: `https://cdn.jsdelivr.net/npm/@fancyapps/ui@5.0/dist/`
    *   文件 `fancybox.umd.js` -> 放入 `static/js/`
    *   文件 `fancybox.css` -> 放入 `static/css/`
*   **Dropzone**:
    *   下载地址: `https://unpkg.com/dropzone@5/dist/min/`
    *   文件 `dropzone.min.js` -> 放入 `static/js/`
    *   文件 `dropzone.min.css` -> 放入 `static/css/`
---

## 📝 使用说明

1. 访问服务器地址后，可以看到文件浏览界面
2. 左侧边栏支持文件拖拽上传和创建新文件夹
3. 主界面支持：
   - 文件/文件夹浏览
   - 排序（按名称、大小、修改日期）
   - 批量选择和操作
   - 全局搜索
   - 文件预览（文本和图片）
4. 支持多选文件后进行批量下载或删除操作

## 🔒 安全说明

- 可以设置访问密码保护服务器
- 程序具有基础的路径遍历攻击防护
- 会话管理确保用户登录状态安全

## 🤝 贡献

欢迎提交 Issue 和 Pull Request 来改进这个项目。

## 📄 许可证

本项目仅供个人学习和使用，请勿用于商业用途。
