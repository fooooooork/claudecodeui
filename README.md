# Claude Code UI

<div align="center">
  <img src="public/logo.svg" alt="Claude Code UI" width="64" height="64">
  <h1>Claude Code UI</h1>
  <p>为 Claude Code CLI 提供现代化的 Web 界面</p>
</div>

## 项目概述

Claude Code UI 是一个基于 Web 的桌面和移动端界面，为 Anthropic 官方的 Claude Code CLI 提供图形化操作体验。它允许你通过浏览器本地或远程访问 Claude Code 项目，管理会话，编辑文件，并与 Claude AI 进行交互式对话。

## 技术栈

### 前端技术栈
- **React 18** - 现代组件架构，使用 Hooks 和 Context API
- **Vite** - 快速构建工具和开发服务器
- **Tailwind CSS** - 实用优先的 CSS 框架，支持暗色模式
- **CodeMirror** - 高级代码编辑器，支持多语言语法高亮
- **React Router DOM** - 客户端路由管理
- **WebSocket** - 实时双向通信
- **React Markdown** - Markdown 内容渲染
- **Lucide React** - 现代化图标库
- **React Dropzone** - 文件拖拽上传

### 后端技术栈
- **Node.js** - JavaScript 运行时环境
- **Express.js** - Web 应用框架，提供 RESTful API
- **WebSocket (ws)** - 实时通信协议
- **SQLite (better-sqlite3)** - 轻量级关系型数据库
- **bcrypt** - 密码哈希加密
- **JWT** - JSON Web Token 身份验证
- **node-pty** - 伪终端支持，用于 Shell 集成
- **chokidar** - 文件系统监听，实时项目更新
- **multer** - 文件上传处理

### 开发工具
- **Concurrently** - 并行运行前后端服务
- **PostCSS** - CSS 后处理器
- **Autoprefixer** - CSS 浏览器前缀自动添加

## 业务逻辑

### 核心功能模块

#### 1. 项目管理
- **自动发现** - 从 `~/.claude/projects/` 自动扫描 Claude Code 项目
- **项目浏览** - 可视化项目列表，显示元数据和会话数量
- **项目操作** - 重命名、删除、手动添加项目
- **智能导航** - 快速访问最近的项目和会话

#### 2. 会话管理
- **会话持久化** - 所有对话自动保存到本地存储
- **会话组织** - 按项目和时间戳分组管理
- **会话操作** - 重命名、删除、导出对话历史
- **跨设备同步** - 从任何设备访问会话

#### 3. 聊天界面
- **实时通信** - 通过 WebSocket 与 Claude AI 实时对话
- **消息历史** - 完整的对话历史记录，包含时间戳和元数据
- **多格式支持** - 文本、代码块、文件引用
- **会话保护** - 防止项目更新中断活跃对话

#### 4. 文件管理
- **交互式文件树** - 可展开/折叠的项目结构导航
- **实时文件编辑** - 直接在界面中读取、修改和保存文件
- **语法高亮** - 支持多种编程语言
- **文件操作** - 创建、重命名、删除文件和目录

#### 5. 终端集成
- **内置 Shell** - 直接访问 Claude Code CLI
- **伪终端支持** - 完整的终端功能，包括命令历史
- **实时输出** - 命令执行结果的实时显示

#### 6. Git 集成
- **版本控制** - 查看、暂存和提交更改
- **分支管理** - 切换和管理 Git 分支
- **状态显示** - 实时显示文件变更状态

### 安全机制

#### 工具配置
- **默认禁用** - 所有 Claude Code 工具默认禁用，防止潜在危险操作
- **选择性启用** - 用户可手动启用需要的工具
- **本地存储** - 工具偏好设置保存在本地

#### 身份验证
- **JWT 令牌** - 基于令牌的身份验证
- **密码加密** - bcrypt 哈希密码存储
- **会话管理** - 安全的用户会话处理

## 快速开始

### 环境要求

- **Node.js** v20 或更高版本
- **Claude Code CLI** 已安装并配置
- **Git** (可选，用于版本控制)

### 安装步骤

1. **克隆仓库**
```bash
git clone https://github.com/siteboon/claudecodeui.git
cd claudecodeui
```

2. **安装依赖**
```bash
npm install
```

3. **配置环境变量**
```bash
cp .env.example .env
# 编辑 .env 文件，设置端口和其他配置
```

4. **启动应用**

开发模式（热重载）：
```bash
npm run dev
```

生产模式：
```bash
npm run build
npm start
```

5. **访问应用**
- 开发环境：`http://localhost:3001`
- 生产环境：根据配置的端口访问

### 环境变量配置

创建 `.env` 文件并配置以下变量：

```env
# 服务器端口
PORT=3002

# 前端开发服务器端口
VITE_PORT=3001

# 数据库路径（可选）
DB_PATH=./server/database/auth.db

# JWT 密钥（生产环境必须设置）
JWT_SECRET=your-secret-key
```

## 使用指南

### 首次使用

1. **启动应用** - 运行 `npm run dev`
2. **访问界面** - 打开浏览器访问 `http://localhost:3001`
3. **配置工具** - 在侧边栏设置中启用需要的 Claude Code 工具
4. **选择项目** - 从项目列表中选择要工作的项目
5. **开始对话** - 使用聊天界面与 Claude AI 交互

### 核心操作

#### 项目管理
- **查看项目** - 侧边栏显示所有可用项目
- **创建会话** - 点击项目创建新的对话会话
- **管理会话** - 重命名、删除或导出会话历史

#### 文件操作
- **浏览文件** - 使用文件树导航项目结构
- **编辑文件** - 点击文件在代码编辑器中打开
- **保存更改** - 使用 Ctrl+S 或点击保存按钮

#### 终端使用
- **打开终端** - 点击 Shell 按钮打开内置终端
- **执行命令** - 直接运行 Claude Code CLI 命令
- **查看输出** - 实时查看命令执行结果

#### Git 操作
- **查看状态** - 在 Git 面板查看文件变更
- **暂存文件** - 选择要暂存的文件
- **提交更改** - 添加提交信息并提交

## 架构设计

### 系统架构

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   前端界面      │    │   后端服务      │    │  Claude CLI     │
│   (React/Vite)  │◄──►│ (Express/WS)    │◄──►│   集成          │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

### 数据流

1. **项目发现** - 后端监听 `~/.claude/projects/` 目录变化
2. **实时通信** - WebSocket 连接处理聊天和项目更新
3. **文件操作** - RESTful API 处理文件读写操作
4. **会话管理** - SQLite 数据库存储用户和会话信息

### 安全设计

- **工具隔离** - 默认禁用所有工具，用户选择性启用
- **文件权限** - 限制文件操作范围，防止系统文件访问
- **会话保护** - 防止项目更新中断活跃对话
- **输入验证** - 所有用户输入进行验证和清理

## 开发指南

### 项目结构

```
claudecodeui/
├── src/                    # 前端源码
│   ├── components/         # React 组件
│   ├── contexts/          # React Context
│   ├── hooks/             # 自定义 Hooks
│   ├── utils/             # 工具函数
│   └── lib/               # 第三方库配置
├── server/                # 后端源码
│   ├── routes/            # API 路由
│   ├── middleware/        # 中间件
│   ├── database/          # 数据库相关
│   └── claude-cli.js     # Claude CLI 集成
├── public/                # 静态资源
└── dist/                  # 构建输出
```

### 开发命令

```bash
# 开发模式（前后端并行）
npm run dev

# 仅启动后端
npm run server

# 仅启动前端
npm run client

# 构建生产版本
npm run build

# 预览构建结果
npm run preview
```

## 故障排除

### 常见问题

#### 1. 找不到 Claude 项目
**问题**：界面显示没有项目或空的项目列表
**解决方案**：
- 确保 Claude CLI 已正确安装
- 在至少一个项目目录中运行 `claude` 命令初始化
- 验证 `~/.claude/projects/` 目录存在且有正确权限

#### 2. 文件浏览器问题
**问题**：文件无法加载、权限错误、空目录
**解决方案**：
- 检查项目目录权限
- 验证项目路径存在且可访问
- 查看服务器控制台日志获取详细错误信息

#### 3. WebSocket 连接失败
**问题**：聊天功能无法正常工作
**解决方案**：
- 检查防火墙设置
- 验证端口配置
- 重启开发服务器

## 许可证

GNU General Public License v3.0 - 详见 [LICENSE](LICENSE) 文件。

## 致谢

### 构建技术
- **[Claude Code](https://docs.anthropic.com/en/docs/claude-code)** - Anthropic 官方 CLI
- **[React](https://react.dev/)** - 用户界面库
- **[Vite](https://vitejs.dev/)** - 快速构建工具
- **[Tailwind CSS](https://tailwindcss.com/)** - 实用优先的 CSS 框架
- **[CodeMirror](https://codemirror.net/)** - 高级代码编辑器

---

<div align="center">
  <strong>为 Claude Code 社区精心打造</strong>
</div>
