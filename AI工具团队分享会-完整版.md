# AI工具团队分享会 - 2025完整指南

> 📌 **2025年10月最新版** - 涵盖所有主流AI工具，包含MCP、Agent、Prompt、Rules详解
> 
> 📅 2025年10月4日 | 📊 适用于研发、产品、设计团队

---

## 🚀 快速导航 - 按角色选择

| 角色 | 推荐工具 | 说明 |
|-----|---------|------|
| 👶 **完全小白** | Kimi（免费） | 200万字超长上下文，完全免费，国内直接访问 |
| 👨‍💻 **程序员** | Cursor + Claude 4 | 最强编程组合，支持MCP、Agent、完整的Rules配置 |
| 🎨 **UI设计师** | v0.dev + Stitch | 设计稿直接转代码，生成React/Next.js组件 |
| 👨‍💼 **产品经理** | ChatGPT + Notion AI | PRD撰写、会议纪要、需求管理 |
| 🎬 **视频/设计** | Sora 2 + 剪映 | AI视频生成 + 免费剪辑工具 |

---

## 📋 目录

- [核心概念解释](#核心概念解释)
  - [MCP (Model Context Protocol)](#mcp-model-context-protocol)
  - [AI Agent](#ai-agent)
  - [Prompt (提示词)](#prompt-提示词)
  - [Rules (规则)](#rules-规则)
- [编程开发工具](#编程开发工具)
  - [Cursor](#1-cursor---ai原生代码编辑器)
  - [Claude 4](#2-claude-4-sonnet---最强编程ai)
  - [GitHub Copilot](#3-github-copilot---实时代码补全)
  - [Gemini 2.5 Pro](#4-gemini-25-pro---google多模态ai)
  - [Grok 4](#5-grok-4---xai最新模型)
- [UI代码生成工具](#ui代码生成工具)
  - [v0.dev](#1-v0dev---vercel官方ui生成器)
  - [Stitch](#2-stitch---google设计转代码工具)
  - [bolt.new](#3-boltnew---stackblitz全栈应用生成)
  - [Lovable](#4-lovable---ai全栈开发)
  - [Replit Agent](#5-replit-agent---在线ai协作开发)
- [小白/通用工具](#小白通用工具)
  - [Kimi](#1-kimi---月之暗面超长上下文ai)
  - [通义千问](#2-通义千问---阿里云多模态ai)
  - [豆包](#3-豆包---字节跳动ai助手)
  - [ChatGPT](#4-chatgpt---openai经典ai)
  - [Perplexity AI](#5-perplexity-ai---ai搜索引擎)
- [设计/图像/视频工具](#设计图像视频工具)
  - [Sora 2](#1-sora-2---openai视频生成)
  - [剪映](#2-剪映---视频剪辑ai工具)
  - [Canva](#3-canva---零基础设计工具)
  - [Midjourney](#4-midjourney---最强ai图像生成)
  - [DALL·E 3](#5-dalle-3---openai图像生成)
  - [Runway ML](#6-runway-ml---ai视频编辑)
- [价格汇总](#价格汇总)

---

<div id="核心概念解释"></div>

## 📚 核心概念解释（必读）

在使用AI工具之前，先理解这4个核心概念，它们决定了你能否高效使用AI工具：

---

<div id="mcp-model-context-protocol"></div>

### 1️⃣ MCP (Model Context Protocol) - 模型上下文协议

#### 💡 是什么？

Anthropic开发的开放协议，让AI能连接外部数据源。**就像给AI装了"USB接口"**，可以插入各种工具和数据。

#### 🎯 能做什么？

- ✅ 让Claude直接读取你的本地文件系统
- ✅ 连接数据库（MySQL、PostgreSQL等）
- ✅ 集成外部服务（GitHub、Notion、Google Drive）
- ✅ 调用自定义API和工具
- ✅ 实时获取最新数据

#### 📌 对比示例

**❌ 没有MCP：**
```
你：复制代码 → 粘贴给AI → AI分析 → 你再粘贴回去
```

**✅ 使用MCP：**
```
你：让AI直接读取项目 → AI自动分析所有文件 → AI直接修改文件
```

#### 🔧 支持MCP的工具

- **Claude Desktop**（原生支持）
- **Cursor**（通过MCP服务器）

#### 📝 MCP配置示例

**Claude Desktop配置文件位置：**
- macOS: `~/Library/Application Support/Claude/claude_desktop_config.json`
- Windows: `%APPDATA%\Claude\claude_desktop_config.json`

**配置示例：**
```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/path/to/project"]
    },
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_TOKEN": "your_token_here"
      }
    }
  }
}
```

---

<div id="ai-agent"></div>

### 2️⃣ AI Agent - AI代理

#### 💡 是什么？

能**自主规划、执行多步骤任务**的AI系统。不只是回答问题，而是主动完成复杂任务。

#### 🎯 能做什么？

- ✅ 自动分解复杂任务为多个步骤
- ✅ 调用多个工具和API
- ✅ 自我纠错和迭代优化
- ✅ 并行处理多个子任务
- ✅ 生成完整的解决方案

#### 📌 对比示例

**❌ 普通AI对话：**
```
你："这段代码有bug吗？"
AI："有，第12行空指针异常"
你："怎么修？"
AI："改成这样..."
```

**✅ AI Agent：**
```
你："帮我修复项目中的所有bug并优化性能"

AI Agent自动：
  1. 扫描所有代码文件
  2. 静态分析找出潜在bug
  3. 自动修复每个问题
  4. 运行测试验证修复
  5. 性能分析找出瓶颈
  6. 优化慢查询和算法
  7. 生成详细修复报告
```

#### 🔧 支持Agent的工具

- **Cursor**（Background Agent）
- **bolt.new**（自动生成完整项目）
- **GitHub Copilot Workspace**

---

<div id="prompt-提示词"></div>

### 3️⃣ Prompt - 提示词/指令

#### 💡 是什么？

你给AI的指令、问题或要求。**决定了AI理解需求和输出质量的关键**。

#### 🎯 好Prompt的特征

- ✅ 清晰具体的需求描述
- ✅ 提供充足的上下文信息
- ✅ 明确期望的输出格式
- ✅ 包含约束条件和边界情况

#### 📌 对比示例

**❌ 差的Prompt：**
```
"帮我写个函数"
```

**✅ 好的Prompt：**
```
用TypeScript写一个异步函数getUserById：
- 输入：userId (string类型)
- 功能：从PostgreSQL数据库查询用户信息
- 输出：返回User对象（包含id, name, email字段）
- 错误处理：用户不存在返回null，数据库错误抛出异常
- 使用Prisma ORM
- 添加JSDoc注释
```

#### 🔧 Prompt工程技巧

1. **角色扮演**："你是一个资深的Python架构师..."
2. **分步指导**："第一步...第二步...第三步..."
3. **Few-shot示例**：提供2-3个示例让AI理解模式
4. **思维链**："让我们一步步思考..."
5. **格式约束**："用Markdown表格输出结果"

---

<div id="rules-规则"></div>

### 4️⃣ Rules - 规则/代码规范

#### 💡 是什么？

给AI设定的行为规范和代码标准。在Cursor中是**`.cursorrules`文件**。让AI自动遵循团队的编码规范。

#### 🎯 能做什么？

- ✅ 统一团队代码风格
- ✅ 自动应用最佳实践
- ✅ 强制类型安全
- ✅ 禁止不安全的代码模式
- ✅ 自定义命名规范

#### 📌 .cursorrules文件示例

**创建`.cursorrules`文件：**

```
# TypeScript项目规则

## 代码风格
- 使用4空格缩进，不用Tab
- 所有函数必须有TypeScript类型注解
- 变量名使用camelCase，常量用UPPER_SNAKE_CASE
- 接口名以I开头，如IUser

## 异步处理
- 必须使用async/await，禁止使用回调函数
- 所有Promise必须有错误处理

## 错误处理
- 使用try-catch包裹可能出错的代码
- 自定义错误要继承Error类
- 记录详细的错误日志

## 安全
- 禁止使用eval()
- 禁止SQL字符串拼接，使用参数化查询
- 所有用户输入必须验证和清理

## 测试
- 每个函数都要有单元测试
- 测试覆盖率不低于80%

## 注释
- 公共API必须有JSDoc注释
- 复杂逻辑要有行内注释说明
```

#### 效果展示

**✅ AI会自动生成符合规则的代码：**
```typescript
async function getUserById(userId: string): Promise<IUser | null> {
  try {
    const user = await db.user.findUnique({
      where: { id: userId }
    });
    return user;
  } catch (error) {
    logger.error('Failed to get user', { userId, error });
    throw new DatabaseError('User query failed');
  }
}
```

**❌ AI不会生成违反规则的代码：**
```typescript
function getUser(id, callback) {  // 违反：没类型、用回调
  db.query("SELECT * FROM users WHERE id=" + id, callback);  // 违反：SQL注入
}
```

---

<div id="编程开发工具"></div>

## 🖥️ 编程开发工具（程序员必备）

---

### 1. Cursor - AI原生代码编辑器 ⭐⭐⭐⭐⭐

#### 💡 主要特点

- 基于VS Code深度定制，AI功能原生集成
- 支持多模型切换（Claude 4、GPT-4o、Gemini 2.5等）
- `Ctrl+K` 内联编辑，`Ctrl+L` 对话式编程
- `@符号` 引用文件/文件夹上下文
- **Background Agent** 自动化处理复杂任务

#### 🤖 MCP支持

- ✅ 通过MCP服务器连接外部数据源
- ✅ 读取本地文件系统
- ✅ 连接数据库和API
- 配置方式：在设置中添加MCP服务器配置

#### 🎯 AI Agent能力

**Background Agent模式**：并行处理多个任务

示例："帮我重构整个项目使用TypeScript"

Agent会：
1. 扫描所有文件
2. 逐个转换为TypeScript
3. 修复类型错误
4. 更新配置文件

#### ✍️ Prompt最佳实践

**❌ 差的：**
```
"优化这段代码"
```

**✅ 好的：**
```
"重构这个函数，要求：
1. 使用async/await替代Promise.then
2. 添加完整的错误处理
3. 优化数据库查询，减少N+1问题
4. 添加TypeScript类型注解
5. 保持原有功能不变"
```

#### 📋 Rules配置示例

创建 `.cursorrules` 文件：

```
# 项目: E-commerce API
# 技术栈: Node.js + TypeScript + Prisma + PostgreSQL

## 代码规范
- 使用TypeScript strict模式
- 所有异步函数使用async/await
- 接口命名: I前缀，如IUser, IProduct
- 枚举命名: 大写下划线，如USER_STATUS
- 文件命名: kebab-case, 如user-service.ts

## 架构模式
- 使用三层架构: Controller -> Service -> Repository
- 每层独立测试
- 依赖注入使用tsyringe

## 数据库
- 使用Prisma ORM
- 所有查询必须有类型安全
- 复杂查询写成raw SQL并注明原因

## 错误处理
- 自定义错误类: AppError, ValidationError, DatabaseError
- Controller层捕获错误并返回HTTP状态码
- 记录所有错误到日志系统

## 安全
- 所有API需要认证中间件
- 输入验证使用zod
- 防止SQL注入，使用参数化查询
- 敏感数据不输出到日志

## 测试
- 单元测试覆盖率>80%
- 使用Jest框架
- Mock外部依赖
```

#### 🎯 适用任务

- ✅ 快速理解陌生代码库（@folders整个项目）
- ✅ 实时代码补全和生成
- ✅ 大规模代码重构
- ✅ Bug定位和修复
- ✅ 代码审查和安全检查
- ✅ 自动化测试生成

#### 💰 收费情况

- **免费版**：基础代码补全，有使用次数限制
- **Pro版**：$20/月，无限使用所有模型，优先响应，支持Background Agent
- **Team版**：$40/月/人，团队协作 + 代码库索引 + 共享Rules

#### 🌐 访问方式

- **官网**：https://cursor.so
- **支持平台**：Windows / macOS / Linux
- 下载后直接安装，可导入VS Code配置

#### 📌 高级使用技巧

1. **使用@符号精准引用**：
   - `@filename.ts` - 引用单个文件
   - `@folders src/` - 引用整个目录
   - `@docs README.md` - 引用文档

2. **组合使用Ctrl+K和Ctrl+L**：
   - Ctrl+K：快速局部修改
   - Ctrl+L：复杂问题讨论和方案设计

3. **Background Agent工作流**：
   - 创建详细的任务描述
   - 启动Background Agent
   - Agent自动分解任务并执行
   - 实时查看进度
   - Review并合并修改

---

### 2. Claude 4 Sonnet - 最强编程AI ⭐⭐⭐⭐⭐

#### 💡 主要特点

- Anthropic 2025最新模型，编程能力业界最强
- **200K tokens** 超长上下文（约15万字代码）
- 支持多模态（代码、文档、图表、PDF、图片）
- **思维链推理**：展示思考过程
- **Projects功能**：管理长期项目知识库

#### 🤖 MCP支持

- ✅ **原生支持MCP**（Anthropic自己开发的协议）
- ✅ Claude Desktop可配置MCP服务器
- ✅ 连接文件系统、数据库、API

#### 🎯 AI Agent能力

**多步骤推理**：自动分解复杂任务

示例：你："帮我创建一个完整的用户认证系统"

Claude Agent会：
1. 设计数据库schema
2. 生成Prisma模型
3. 实现JWT认证逻辑
4. 创建注册/登录API
5. 添加密码加密
6. 编写单元测试
7. 生成API文档

#### ✍️ Prompt工程

**Claude特别擅长的Prompt模式：**

**1. XML标签结构化：**
```xml
<task>
  <context>
    我有一个Express项目，需要添加用户认证
  </context>
  <requirements>
    - 使用JWT token
    - 密码要bcrypt加密
    - 支持刷新token
    - 包含权限验证中间件
  </requirements>
  <constraints>
    - 使用TypeScript
    - 遵循RESTful规范
    - 错误处理要完善
  </constraints>
  <output_format>
    1. 先给出整体架构说明
    2. 然后逐个文件提供代码
    3. 最后给出测试用例
  </output_format>
</task>
```

**2. 角色+思维链：**
```
你是一位拥有20年经验的系统架构师。

请分析这段代码的性能问题，并提供优化方案。

请按以下步骤思考：
1. 识别性能瓶颈
2. 分析根本原因
3. 提出多个优化方案
4. 比较各方案优缺点
5. 给出推荐方案和实现代码
```

**3. Few-shot示例：**
```
我需要你把函数转换为TypeScript：

示例1：
输入：function add(a, b) { return a + b; }
输出：function add(a: number, b: number): number { return a + b; }

示例2：
输入：async function getUser(id) { return await db.users.find(id); }
输出：async function getUser(id: string): Promise<User> { 
  return await db.users.find(id); 
}

现在请转换：
[你的代码]
```

#### 📋 Projects功能（相当于持久化Rules）

创建Project存储项目知识：

```
Project: E-commerce Platform

文档1: 架构设计
- 微服务架构
- 使用gRPC通信
- PostgreSQL + Redis
- Docker部署

文档2: 代码规范
[粘贴你的.cursorrules内容]

文档3: API文档
[粘贴OpenAPI规范]

文档4: 数据库Schema
[粘贴Prisma schema]
```

#### 🎯 适用任务

- ✅ 代码深度审查（性能、安全、可维护性）
- ✅ 系统架构设计和技术选型
- ✅ 大规模代码重构（处理整个代码库）
- ✅ 复杂Bug深度诊断
- ✅ API文档和技术文档生成
- ✅ 代码学习和教学
- ✅ 算法设计和优化

#### 💰 收费情况

- **免费版**：约50次对话/天，使用Claude 4 Sonnet
- **Pro版**：$20/月，5倍使用量，支持所有模型，包含Projects功能
- **API版**：按Token计费，$3输入/$15输出（每百万tokens）

#### 🌐 访问方式

- **网页版**：https://claude.ai
- **Claude Desktop**：https://claude.ai/download
- **API文档**：https://docs.anthropic.com

#### 📌 高级使用技巧

1. **超长上下文利用**：
   - 一次性粘贴整个代码库（200K tokens ≈ 约30个文件）
   - 上传完整技术文档PDF
   - 让Claude理解整个项目后再提问

2. **多模态应用**：
   - 上传架构图让Claude分析设计
   - 上传错误截图让Claude诊断
   - 上传数据库ER图让Claude生成Schema

3. **MCP实战**：
   - "读取我的GitHub仓库所有Issue"
   - "分析我项目的数据库结构"
   - "查看我最近的Git提交"

---

### 3. GitHub Copilot - 实时代码补全 ⭐⭐⭐⭐

#### 💡 主要特点

- OpenAI Codex驱动，实时代码建议
- 深度GitHub集成，理解数百万开源项目模式
- 支持30+主流IDE
- 支持80+编程语言
- **Copilot Chat**：在IDE内对话式编程

#### 🎯 AI Agent能力

**Copilot Workspace**（新功能）：
- 基于GitHub Issue自动生成PR
- 自动规划实现步骤
- 跨文件修改和测试

#### ✍️ Prompt技巧（通过注释）

**在代码中用注释作为Prompt：**
```typescript
// 创建一个React组件，展示用户列表
// 需求：
// 1. 从API获取用户数据
// 2. 支持分页，每页10条
// 3. 支持搜索功能
// 4. 点击用户显示详情弹窗
// 5. 使用TypeScript和Hooks

// Copilot会自动生成完整组件代码
```

**函数名作为Prompt：**
```python
def calculate_user_monthly_subscription_revenue_with_discounts(
    user_id: str,
    month: int,
    year: int,
    apply_promotional_codes: bool = True
):
    # Copilot会根据函数名生成完整实现
```

#### 🎯 适用任务

- ✅ 快速编写样板代码（CRUD、API调用）
- ✅ 根据注释自动实现函数
- ✅ 自动生成单元测试
- ✅ 学习新技术和API用法
- ✅ 代码片段快速生成

#### 💰 收费情况

- **个人版**：$10/月
- **企业版**：$19/月/人，支持代码隐私保护
- **学生/教师**：✅ 免费（需GitHub Education认证）
- **开源维护者**：✅ 免费（需认证）

#### 🌐 访问方式

- **订阅**：https://github.com/features/copilot
- **支持IDE**：VS Code、IntelliJ IDEA、PyCharm、Neovim、Visual Studio
- 在IDE扩展商店搜索"GitHub Copilot"

#### 📌 高级使用技巧

1. **多行补全**：
   - 按 `Tab` 接受建议
   - 按 `Alt+]` 查看下一个建议
   - 按 `Ctrl+Enter` 查看多个建议

2. **Copilot Chat使用**：
   - `/explain` - 解释选中代码
   - `/fix` - 修复bug
   - `/tests` - 生成测试
   - `/doc` - 生成文档

---

### 4. Gemini 2.5 Pro - Google多模态AI ⭐⭐⭐⭐

#### 💡 主要特点

- Google 2025最新模型
- **200万tokens** 超长上下文（业界最长，约150万字）
- 强大多模态能力（文本、图片、视频、音频、代码）
- 深度集成Google生态
- 实时联网搜索

#### 🎯 适用任务

- ✅ 超大型项目分析（整个代码库）
- ✅ 技术文档PDF快速提取信息
- ✅ 架构图分析和优化建议
- ✅ 多文件代码审查
- ✅ 视频教程内容提取

#### 💰 收费情况

- **免费版**：Gemini 2.0 Flash，有使用限制
- **Gemini Advanced**：$19.99/月，Gemini 2.5 Pro，2TB Google One存储
- **API版**：$1.25输入/$5输出（每百万tokens）

#### 🌐 访问方式

- **网页版**：https://gemini.google.com
- **API文档**：https://ai.google.dev/docs

---

### 5. Grok 4 - xAI最新模型 ⭐⭐⭐

#### 💡 主要特点

- Elon Musk的xAI团队开发
- 与X平台（Twitter）深度集成
- **实时联网**，获取最新技术动态
- 回答风格幽默

#### 🎯 适用任务

- ✅ 了解最新技术趋势和新闻
- ✅ 代码生成和调试
- ✅ 技术问题解答
- ✅ 创意编程方案

#### 💰 收费情况

- **需要X Premium+订阅**：$16/月（包含X平台所有Premium功能）

#### 🌐 访问方式

- **方式1**：https://x.com - 登录后侧边栏找到Grok
- **方式2**：https://grok.x.ai

---

<div id="ui代码生成工具"></div>

## 🎨 UI代码生成工具（前端开发神器）

---

### 1. v0.dev - Vercel官方UI生成器 ⭐⭐⭐⭐⭐

#### 💡 主要特点

- Vercel官方出品，专注前端UI生成
- 生成高质量React/Next.js/TypeScript代码
- 支持Tailwind CSS、shadcn/ui组件库
- 实时预览，一键复制代码

#### ✍️ Prompt示例

```
"创建一个现代风格的登录页面
要求：
- 使用Next.js 14 App Router
- Tailwind CSS样式
- 包含邮箱、密码输入框
- Google和GitHub第三方登录按钮
- 响应式设计，支持手机端
- 深色模式支持
- 表单验证用react-hook-form + zod
- 添加加载状态和错误提示
- 参考Vercel登录页设计风格"
```

#### 🎯 适用任务

- ✅ 快速搭建页面UI界面
- ✅ 生成React组件代码
- ✅ 创建表单、卡片、导航等组件
- ✅ 快速原型开发

#### 💰 收费情况

- **免费版**：200积分/月（约20-30个组件）
- **付费版**：$20/月，5000积分/月

#### 🌐 访问方式

- **官网**：https://v0.dev

---

### 2. Stitch - Google设计转代码工具 ⭐⭐⭐⭐⭐

#### 💡 主要特点

- Google官方出品，Figma到代码的桥梁
- AI理解设计稿，生成高质量代码
- 支持React、Vue、Angular
- Material Design风格原生支持

#### 🎯 适用任务

- ✅ Figma设计稿转代码
- ✅ 设计系统实现
- ✅ UI组件库开发
- ✅ 保持设计与代码一致

#### 💰 收费情况

- **免费版**：基础功能
- **Pro版**：定价见官网

#### 🌐 访问方式

- **官网**：https://stitch.withgoogle.com
- Figma插件商店搜索"Stitch"

---

### 3. bolt.new - StackBlitz全栈应用生成 ⭐⭐⭐⭐⭐

#### 💡 主要特点

- StackBlitz出品，生成完整Web应用
- 支持React、Vue、Node.js等技术栈
- 在线IDE环境，实时运行预览

#### ✍️ Prompt示例

```
"创建一个任务管理Web应用：

前端：
- React + TypeScript + Vite
- Tailwind CSS样式
- 用户可以添加、编辑、删除任务
- 任务有状态：待办、进行中、已完成
- 支持拖拽排序
- 本地存储用localStorage

请生成完整可运行的项目"
```

#### 💰 收费情况

- **免费版**：有使用次数限制
- **付费版**：$20/月，无限使用

#### 🌐 访问方式

- **官网**：https://bolt.new

---

### 4. Lovable - AI全栈开发 ⭐⭐⭐⭐

#### 💡 主要特点

- 从自然语言描述生成完整应用
- 支持React、Next.js、Supabase
- 自动部署到云端

#### 💰 收费情况

- **Hobby版**：$29/月
- **Pro版**：$99/月

#### 🌐 访问方式

- **官网**：https://lovable.dev

---

### 5. Replit Agent - 在线AI协作开发 ⭐⭐⭐⭐

#### 💡 主要特点

- 在线IDE + AI编程助手
- 支持50+编程语言
- 实时协作，多人同时编辑

#### 💰 收费情况

- **免费版**：有资源限制
- **Core版**：$7/月

#### 🌐 访问方式

- **官网**：https://replit.com

---

<div id="小白通用工具"></div>

## 👶 小白/通用AI工具（推荐从这里开始！）

---

### 1. Kimi - 月之暗面超长上下文AI ⭐⭐⭐⭐⭐

#### 💡 主要特点

- 国产AI，月之暗面（Moonshot AI）出品
- **200万字**超长上下文（约4本《红楼梦》）
- 可以一次性读完整本书、长论文
- 中文理解能力极强
- **完全免费**，无使用限制

#### 🎯 适用任务

- ✅ 长文档阅读和总结（论文、报告、合同）
- ✅ 学习资料整理（上传PDF、Word）
- ✅ 日常聊天问答
- ✅ 写作辅助（文章、报告、总结）
- ✅ 翻译（中英互译）
- ✅ 代码解释和学习

#### 💰 收费情况

- ✅ **完全免费**，无任何限制！

#### 🌐 访问方式

- **官网**：https://kimi.moonshot.cn
- 无需科学上网，国内直接访问
- 支持手机号/微信登录
- 有网页版和APP

#### 📌 使用技巧

- 上传PDF/Word文档，Kimi会自动阅读并回答问题
- 适合处理超长文档，如论文、合同、技术文档
- 问："总结这篇文章的核心观点"
- 问："找出文档中的关键数据"

---

### 2. 通义千问 - 阿里云多模态AI ⭐⭐⭐⭐⭐

#### 💡 主要特点

- 阿里云出品，技术实力强
- 支持多模态（文字、图片、文档）
- 深度集成阿里生态（钉钉、钉盘）

#### 🎯 适用任务

- ✅ 办公文档处理（Word、Excel、PPT）
- ✅ 图片理解和分析
- ✅ 代码辅助

#### 💰 收费情况

- **免费版**：功能完整，日常使用足够
- **Plus版**：¥60/月，更快响应

#### 🌐 访问方式

- **官网**：https://tongyi.aliyun.com

---

### 3. 豆包 - 字节跳动AI助手 ⭐⭐⭐⭐

#### 💡 主要特点

- 字节跳动出品，技术成熟
- 完全免费，无任何使用限制
- 响应速度快

#### 🎯 适用任务

- ✅ 日常聊天对话
- ✅ 写作辅助
- ✅ 知识问答

#### 💰 收费情况

- ✅ **完全免费**，无限制使用！

#### 🌐 访问方式

- **官网**：https://doubao.com

---

### 4. ChatGPT - OpenAI经典AI ⭐⭐⭐⭐⭐

#### 💡 主要特点

- OpenAI出品，全球最流行的AI
- 功能全面，插件生态丰富
- 支持联网搜索、数据分析、图像生成

#### 🎯 适用任务

- ✅ 通用对话和问答
- ✅ 写作（文章、代码、创意文案）
- ✅ 数据分析（上传Excel/CSV）
- ✅ 图像生成
- ✅ 联网搜索最新信息

#### 💰 收费情况

- **免费版**：GPT-4o mini，有使用限制
- **Plus版**：$20/月，GPT-4o无限使用，包含DALL·E 3
- **Pro版**：$200/月，o1推理模型无限使用

#### 🌐 访问方式

- **官网**：https://chat.openai.com

---

### 5. Perplexity AI - AI搜索引擎 ⭐⭐⭐⭐

#### 💡 主要特点

- AI驱动的搜索引擎
- 不只给链接，直接给答案
- 每个答案都有引用来源
- 实时联网搜索

#### 🎯 适用任务

- ✅ 搜索资料和学习
- ✅ 了解最新新闻和动态
- ✅ 研究和对比信息

#### 💰 收费情况

- **免费版**：基础搜索功能
- **Pro版**：$20/月，使用GPT-4等高级模型

#### 🌐 访问方式

- **官网**：https://www.perplexity.ai

---

<div id="设计图像视频工具"></div>

## 🎨 设计/图像/视频工具

---

### 1. Sora 2 - OpenAI视频生成 ⭐⭐⭐⭐⭐

#### 💡 主要特点

- OpenAI 2025最新视频生成模型
- 从文字描述生成高质量视频
- 支持最长60秒视频
- 物理规律准确，运动流畅

#### ✍️ Prompt示例

```
"创建一个30秒的产品宣传视频：

场景：现代化办公室
镜头：从窗外推进，展示团队在使用我们的软件
风格：商业广告风格，明亮温暖色调
音乐：轻快的背景音乐
文字：产品名称和Slogan
分辨率：1920x1080"
```

#### 🎯 适用任务

- ✅ 文字生成视频
- ✅ 产品宣传片
- ✅ 教学演示视频
- ✅ 创意视频制作

#### 💰 收费情况

- 定价待官方公布
- 预计包含在ChatGPT Pro订阅中

#### 🌐 访问方式

- **官网**：https://openai.com/sora

---

### 2. 剪映 - 视频剪辑AI工具 ⭐⭐⭐⭐⭐

#### 💡 主要特点

- 字节跳动出品，完全免费
- **自动识别语音生成字幕**
- 智能剪辑，一键成片
- 特效和转场丰富

#### 🎯 适用任务

- ✅ 短视频制作（抖音、快手）
- ✅ Vlog剪辑
- ✅ 教学视频制作
- ✅ 会议录屏加字幕

#### 💰 收费情况

- ✅ **完全免费**（少量会员专属素材）

#### 🌐 访问方式

- 搜索"剪映"下载APP
- 支持Windows、macOS、iOS、Android

---

### 3. Canva - 零基础设计工具 ⭐⭐⭐⭐⭐

#### 💡 主要特点

- 零基础也能做设计
- 海量模板（PPT、海报、社交媒体）
- 拖拽式操作，非常简单
- AI辅助设计

#### 🎯 适用任务

- ✅ PPT制作
- ✅ 海报设计
- ✅ 朋友圈配图
- ✅ 公众号封面
- ✅ 简历制作

#### 💰 收费情况

- **免费版**：基础模板和功能，够用
- **Pro版**：$12.99/月，所有模板+AI功能

#### 🌐 访问方式

- **官网**：https://www.canva.com

---

### 4. Midjourney - 最强AI图像生成 ⭐⭐⭐⭐⭐

#### 💡 主要特点

- 图像质量最高，艺术感最强
- 风格多样，支持各种艺术风格
- 迭代方便，可基于图片继续优化

#### 🎯 适用任务

- ✅ 插画创作
- ✅ 概念设计
- ✅ 海报设计
- ✅ UI设计灵感

#### 💰 收费情况

- **基础版**：$10/月，约200张图
- **标准版**：$30/月，无限生成（放松模式）

#### 🌐 访问方式

- **官网**：https://midjourney.com
- 需要通过Discord使用

---

### 5. DALL·E 3 - OpenAI图像生成 ⭐⭐⭐⭐

#### 💡 主要特点

- OpenAI出品，文字理解准确
- 与ChatGPT深度集成
- 细节控制好

#### 🎯 适用任务

- ✅ 营销素材
- ✅ 广告图
- ✅ 品牌设计

#### 💰 收费情况

- 包含在ChatGPT Plus中（$20/月）

#### 🌐 访问方式

- 通过ChatGPT使用（需Plus会员）

---

### 6. Runway ML - AI视频编辑 ⭐⭐⭐⭐

#### 💡 主要特点

- AI视频生成（文字生成视频）
- 强大的视频特效
- 自动背景替换

#### 🎯 适用任务

- ✅ 产品宣传视频
- ✅ 文字生成视频
- ✅ 视频特效制作

#### 💰 收费情况

- **免费版**：有限次数
- **标准版**：$12/月
- **Pro版**：$28/月

#### 🌐 访问方式

- **官网**：https://runwayml.com

---

<div id="价格汇总"></div>

## 💰 价格汇总对比

### 按价格区间分类

| 价格区间 | 工具列表 | 推荐人群 |
|---------|---------|---------|
| **✅ 完全免费** | Kimi、豆包、剪映、通义千问免费版 | 小白首选，功能完整，零成本 |
| **$7-10/月** | GitHub Copilot ($10)、Replit Core ($7) | 学生免费，个人开发者 |
| **$10-20/月** | Midjourney基础 ($10)、Canva Pro ($13)、Grok ($16) | 单功能工具用户 |
| **$20/月** | Cursor Pro、Claude Pro、ChatGPT Plus、Gemini Advanced、v0.dev、bolt.new | 专业用户、重度使用者（**最主流价位**） |
| **$20-30/月** | Midjourney Pro ($30)、Lovable ($29)、Runway ML ($28) | 专业设计师、视频创作者 |
| **$200/月** | ChatGPT Pro | 顶级推理模型o1，企业高级需求 |

### 免费工具推荐组合（零成本）

**小白零成本方案：**
- 💬 日常对话：Kimi / 豆包 / 通义千问（三选一）
- 🎨 做设计：Canva免费版
- 🎬 剪视频：剪映
- 🔍 搜资料：Perplexity AI免费版

**总成本：$0** - 完全免费，满足90%日常需求！

**程序员学生方案（学生免费）：**
- 💻 写代码：GitHub Copilot（学生免费）
- 🤖 AI助手：Claude免费版（50次/天）
- 🎨 UI生成：v0.dev免费版（200积分/月）

**总成本：$0** - 学生身份全免费！

### 专业用户推荐方案

**个人开发者（$20/月）：**
- Cursor Pro ($20/月) 或 Claude Pro ($20/月)
- 选一个即可，满足大部分编程需求

**全能型开发者（$60/月）：**
- Cursor Pro ($20/月)
- Claude Pro ($20/月)
- ChatGPT Plus ($20/月)
- 三个组合使用，效率最高

**设计师方案（$30-50/月）：**
- Canva Pro ($13/月)
- Midjourney标准版 ($30/月)
- 剪映（免费）

---

## ⚠️ 重要提示和最佳实践

### 数据安全

**❗ 不要上传的内容：**
- ❌ 公司机密代码
- ❌ 用户隐私数据
- ❌ 未发布的商业计划
- ❌ 身份证、密码等敏感信息

**✅ 企业使用建议：**
- 选择支持私有化部署的工具（如Tabnine Enterprise）
- 使用企业版工具，有数据保护协议
- 敏感信息脱敏处理

### 学习建议

1. **从免费工具开始**
   - 先用Kimi/豆包体验AI对话
   - 再用Canva/剪映体验AI创作
   - 最后根据需求选择付费工具

2. **不要过度依赖AI**
   - AI是辅助工具，不是替代品
   - AI生成的内容需要人工审核
   - 保持批判性思维

3. **善用AI学习**
   - 遇到不懂的代码，问AI解释
   - 让AI教你新技术
   - 用AI做学习助手

### 选择建议

**如何选择合适的AI工具？**

1. **看需求场景**
   - 日常对话 → Kimi/豆包（免费）
   - 写代码 → Cursor + Claude
   - 生成UI → v0.dev / Stitch
   - 做设计 → Canva / Midjourney

2. **看预算**
   - 预算有限 → 优先用免费工具
   - 专业用户 → 考虑$20/月的主流工具
   - 企业团队 → 选择企业版，有技术支持

3. **看使用频率**
   - 偶尔用 → 免费版够用
   - 每天用 → 付费版更划算
   - 重度用户 → 选Pro版

---

## 📚 学习资源

### 官方文档
- [Claude使用指南](https://docs.anthropic.com)
- [Cursor文档](https://docs.cursor.sh)
- [v0.dev教程](https://v0.dev/docs)
- [MCP协议文档](https://docs.anthropic.com/mcp)

### 社区资源
- [Prompt Engineering指南](https://www.promptingguide.ai)
- [GitHub Copilot最佳实践](https://github.blog)
- [Cursor中文社区](https://learn-cursor.com/)

### 视频教程
- B站搜索："Cursor教程"、"AI编程"、"v0.dev教程"
- YouTube搜索："AI Coding"、"v0.dev tutorial"

---

## 📅 文档更新记录

| 日期 | 版本 | 更新内容 |
|-----|------|----------|
| 2025-10-04 | v1.0 | • 初始版本<br/>• 包含核心概念详解（MCP、Agent、Prompt、Rules）<br/>• 添加Stitch和Sora 2<br/>• 所有工具详细说明<br/>• 完整的导航链接 |

---

## 💬 反馈与建议

如有任何问题或建议，欢迎反馈！

**最后更新：2025年10月4日**

**祝大家使用AI工具愉快，效率翻倍！🚀**