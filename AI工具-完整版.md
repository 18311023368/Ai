# AI工具团队分享会 - 2025完整指南

> 📌 **2025年10月最新版** - 涵盖所有主流AI工具，包含MCP、Agent、Prompt、Rules详解
> 
> 📅 2025年10月4日 | 📊 适用于研发、产品、设计团队

---

## 🚀 快速导航 - 按角色选择

| 角色 | 推荐工具 | 说明 |
|-----|---------|------|
| 👶 **完全小白** | Kimi（免费） | 200万字超长上下文，完全免费，国内直接访问 |
| 👨‍💻 **程序员** | Cursor + Claude 4 + AI Studio（免费） | 最强编程组合，支持MCP、Agent，完全免费 |
| 🎨 **UI设计师** | Stitch（免费） | Google出品，设计稿自动生成代码 |
| 👨‍💼 **产品经理** | ChatGPT + Notion AI | PRD撰写、会议纪要、需求管理 |

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
  - [AI Studio](#3-ai-studio---google免费ai工具)
  - [Grok](#4-grok---xai最新模型)
  - [Gemini CLI](#5-gemini-cli---命令行ai工具)
  - [TRAE](#6-trae---轻量级ai编程助手)
  - [Codex](#7-codex---openai代码模型)
- [UI代码生成工具](#ui代码生成工具)
  - [Stitch](#1-stitch---google设计转代码工具)
- [小白/通用工具](#小白通用工具)
  - [Kimi](#1-kimi---月之暗面超长上下文ai)
  - [通义千问](#2-通义千问---阿里云多模态ai)
  - [豆包](#3-豆包---字节跳动ai助手)
  - [ChatGPT](#4-chatgpt---openai经典ai)
  - [Perplexity AI](#5-perplexity-ai---ai搜索引擎)
- [设计/图像/视频工具](#设计图像视频工具)
  - [剪映](#1-剪映---视频剪辑ai工具)
  - [Canva](#2-canva---零基础设计工具)
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

### 3. AI Studio - Google免费AI工具 ⭐⭐⭐⭐⭐

#### 💡 主要特点

- **Google官方出品，完全免费**
- 基于Gemini 2.0模型，能力强大
- 支持超长上下文（200万tokens）
- 多模态支持（文本、代码、图片）
- 无使用次数限制

#### 🎯 适用任务

- ✅ 代码生成和调试
- ✅ 技术问题解答
- ✅ 代码审查和优化
- ✅ 学习新技术
- ✅ API文档查询

#### 💰 收费情况

- ✅ **完全免费！** 无任何使用限制

#### 🌐 访问方式

- **官网**：https://aistudio.google.com/prompts/new_chat
- 无需科学上网，直接访问

---

### 4. Grok - xAI最新模型 ⭐⭐⭐⭐⭐

#### 💡 主要特点

- Elon Musk的xAI团队开发
- **完全免费使用**（无需Premium）
- **实时联网**，获取最新技术动态
- 强大的代码能力
- 回答风格直接高效

#### 🎯 适用任务

- ✅ 了解最新技术趋势和新闻
- ✅ 代码生成和调试
- ✅ 技术问题解答
- ✅ 创意编程方案
- ✅ 实时信息查询

#### 💰 收费情况

- ✅ **完全免费！** 基础版无限制使用

#### 🌐 访问方式

- **官网**：https://grok.com/
- 需要X账号登录

---

### 5. Gemini CLI - 命令行AI工具 ⭐⭐⭐⭐

#### 💡 主要特点

- 在命令行直接使用AI
- 快速代码生成和调试
- 支持终端操作自动化
- **完全免费**

#### 🎯 适用任务

- ✅ 终端命令生成
- ✅ 脚本编写辅助
- ✅ 快速代码片段生成
- ✅ Git命令辅助

#### 💰 收费情况

- ✅ **完全免费！**

#### 🌐 访问方式

- 安装：`npm install -g @google/generative-ai-cli`
- 使用：`gemini "你的问题"`

---

### 6. TRAE - 轻量级AI编程助手 ⭐⭐⭐⭐

#### 💡 主要特点

- 轻量级、快速响应
- 专注编程场景
- **完全免费**
- 支持多种编程语言

#### 🎯 适用任务

- ✅ 代码补全
- ✅ Bug修复建议
- ✅ 代码重构
- ✅ 技术文档查询

#### 💰 收费情况

- ✅ **完全免费！**

#### 🌐 访问方式

- **官网**：搜索"TRAE AI"

---

### 7. Codex - OpenAI代码模型 ⭐⭐⭐⭐

#### 💡 主要特点

- OpenAI专门的代码模型
- 支持多种编程语言
- 强大的代码理解能力
- GitHub Copilot的底层模型

#### 🎯 适用任务

- ✅ 代码生成
- ✅ 代码解释
- ✅ 代码转换（语言互转）
- ✅ API调用示例

#### 💰 收费情况

- 通过OpenAI API使用，按token计费
- 或使用GitHub Copilot（$10/月，学生免费）

#### 🌐 访问方式

- **API文档**：https://platform.openai.com/docs

---

<div id="ui代码生成工具"></div>

## 🎨 UI代码生成工具

---

### 1. Stitch - Google设计转代码工具 ⭐⭐⭐⭐⭐

#### 💡 主要特点

- **Google官方出品，完全免费**
- AI自动理解设计稿，生成高质量代码
- 支持React、Vue、Angular等主流框架
- Material Design风格原生支持
- 自动生成响应式布局
- 完美还原设计稿细节

#### 🎯 适用任务

- ✅ Figma/Sketch设计稿自动转代码
- ✅ 设计系统快速实现
- ✅ UI组件库开发
- ✅ 保持设计与代码100%一致
- ✅ 快速原型开发

#### 💰 收费情况

- ✅ **完全免费！** 无任何限制

#### 🌐 访问方式

- **官网**：https://stitch.withgoogle.com
- Figma插件商店搜索"Stitch"
- 支持在线使用和插件集成

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

## 🎨 设计/视频工具

---

### 1. 剪映 - 视频剪辑AI工具 ⭐⭐⭐⭐⭐

#### 💡 主要特点

- **字节跳动出品，完全免费**
- **AI自动识别语音生成字幕**（准确率极高）
- 智能剪辑，一键成片
- 丰富的特效和转场效果
- AI配音、AI文案生成
- 支持多平台使用

#### 🎯 适用任务

- ✅ 短视频制作（抖音、快手、视频号）
- ✅ Vlog剪辑
- ✅ 教学视频制作
- ✅ 会议录屏自动加字幕
- ✅ 去水印、变速、倒放等功能

#### 💰 收费情况

- ✅ **完全免费！**（少量会员专属素材）

#### 🌐 访问方式

- 搜索"剪映"下载APP
- 支持Windows、macOS、iOS、Android

---

### 2. Canva - 零基础设计工具 ⭐⭐⭐⭐⭐

#### 💡 主要特点

- 零基础也能做专业设计
- 海量模板（PPT、海报、社交媒体、简历等）
- 拖拽式操作，非常简单
- AI辅助设计（AI生成图片、AI抠图、AI文案）

#### 🎯 适用任务

- ✅ PPT制作
- ✅ 海报设计
- ✅ 社交媒体配图
- ✅ 公众号封面
- ✅ 简历制作
- ✅ Logo设计

#### 💰 收费情况

- **免费版**：基础模板和功能，日常使用足够
- **Pro版**：$12.99/月，所有模板+AI功能

#### 🌐 访问方式

- **官网**：https://www.canva.com
- 支持网页版和APP

---

<div id="价格汇总"></div>

## 💰 价格汇总对比

### 🎁 完全免费的强大工具（推荐！）

| 工具 | 类型 | 核心功能 |
|-----|------|---------|
| **AI Studio** | AI编程 | Google出品，Gemini 2.0，无限制使用 |
| **Grok** | AI编程 | xAI出品，实时联网，强大代码能力 |
| **Gemini CLI** | 命令行AI | 终端直接使用AI，自动化操作 |
| **TRAE** | 编程助手 | 轻量级，专注编程场景 |
| **Kimi** | 通用AI | 200万字超长上下文，国内直接访问 |
| **豆包** | 通用AI | 字节跳动出品，响应速度快 |
| **剪映** | 视频剪辑 | AI自动字幕，智能剪辑 |
| **Stitch** | UI生成 | Google出品，设计稿自动转代码 |
| **通义千问** | 通用AI | 阿里云出品，办公文档处理强 |

**💡 这些免费工具组合，已经可以满足90%的日常需求！**

---

### 💰 按价格区间分类

| 价格区间 | 工具列表 | 推荐人群 |
|---------|---------|---------|
| **✅ 完全免费** | AI Studio、Grok、Gemini CLI、TRAE、Codex、Kimi、豆包、剪映、Stitch、通义千问 | **所有人首选**，功能强大，零成本 |
| **$20/月** | Cursor Pro、Claude Pro、ChatGPT Plus | 专业用户、重度使用者 |
| **$13/月** | Canva Pro | 需要高级设计模板 |

### 推荐方案

**🎯 零成本完美方案（强烈推荐！）：**
- 💻 **AI编程**：AI Studio（免费） + Grok（免费） + Gemini CLI（免费）
- 🤖 **日常AI**：Kimi（免费） / 豆包（免费）
- 🎨 **UI生成**：Stitch（免费）
- 🎬 **视频剪辑**：剪映（免费）
- 🎨 **图片设计**：Canva免费版

**总成本：$0** - 完全免费，能力超强！

**💎 专业用户方案（$20/月）：**
- Cursor Pro ($20/月) 或 Claude Pro ($20/月)
- 配合免费工具使用，效率最高

**🚀 全能方案（$40/月）：**
- Cursor Pro ($20/月)
- Claude Pro ($20/月)
- 配合所有免费工具，覆盖所有场景

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
| 2025-10-09 | v2.0 | • **大幅简化文档，突出免费工具**<br/>• 新增：AI Studio、Grok、Gemini CLI、TRAE、Codex<br/>• 移除不常用工具，保持简洁实用<br/>• UI工具仅保留Stitch（免费且强大）<br/>• 设计工具仅保留剪映和Canva<br/>• 重点推荐零成本方案 |
| 2025-10-04 | v1.0 | • 初始版本<br/>• 包含核心概念详解（MCP、Agent、Prompt、Rules）<br/>• 所有工具详细说明 |

---

## 💬 反馈与建议

如有任何问题或建议，欢迎反馈！

**最后更新：2025年10月9日**

---

## 🌟 核心推荐总结

### 🎁 完全免费的超强组合

**编程开发：**
- AI Studio（Google免费AI，能力强大）
- Grok（xAI免费，实时联网）
- Gemini CLI（命令行AI工具）
- TRAE（轻量级编程助手）
- Codex（OpenAI代码模型）

**UI和设计：**
- Stitch（Google免费，设计稿自动转代码）
- Canva免费版（零基础设计）
- 剪映（视频剪辑神器）

**日常使用：**
- Kimi（200万字超长上下文）
- 豆包（字节跳动AI）

**💡 以上所有工具完全免费，组合使用，效率爆表！**

---

**祝大家使用AI工具愉快，效率翻倍！🚀**