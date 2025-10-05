# AI工具终极使用指南

> 📌 **2025年10月最新版** - 涵盖所有主流AI工具，包含MCP、Agent、Prompt、Rules详解

---

## 📚 【核心概念解释 - 必读】

在开始之前，先理解这些核心概念：

### 1️⃣ MCP (Model Context Protocol) - 模型上下文协议

**💡 是什么？**
- Anthropic开发的开放协议，让AI能连接外部数据源
- 就像给AI装了"USB接口"，可以插入各种工具和数据源

**🎯 能做什么？**
- ✅ 让Claude直接读取你的本地文件系统
- ✅ 连接数据库（MySQL、PostgreSQL等）
- ✅ 集成外部服务（GitHub、Notion、Google Drive）
- ✅ 调用自定义API和工具
- ✅ 实时获取最新数据

**📌 实际应用：**
```
传统方式：
你：复制代码 → 粘贴给AI → AI分析 → 你再粘贴回去

使用MCP：
你：让AI直接读取项目 → AI自动分析所有文件 → AI直接修改文件
```

**🔧 支持MCP的工具：**
- Claude Desktop (原生支持)
- Cursor (通过MCP服务器)

---

### 2️⃣ AI Agent - AI代理

**💡 是什么？**
- 能自主规划、执行多步骤任务的AI系统
- 不只是回答问题，而是主动完成复杂任务

**🎯 能做什么？**
- ✅ 自动分解复杂任务为多个步骤
- ✅ 调用多个工具和API
- ✅ 自我纠错和迭代优化
- ✅ 并行处理多个子任务
- ✅ 生成完整的解决方案

**📌 实际应用：**
```
普通AI对话：
你："这段代码有bug吗？"
AI："有，第12行空指针异常"
你："怎么修？"
AI："改成这样..."

AI Agent：
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

**🔧 支持Agent的工具：**
- Cursor (Background Agent)
- bolt.new (自动生成完整项目)
- GitHub Copilot Workspace

---

### 3️⃣ Prompt - 提示词/指令

**💡 是什么？**
- 你给AI的指令、问题或要求
- 决定了AI理解需求和输出质量的关键

**🎯 好Prompt的特征：**
- ✅ 清晰具体的需求描述
- ✅ 提供充足的上下文信息
- ✅ 明确期望的输出格式
- ✅ 包含约束条件和边界情况

**📌 对比示例：**

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

**🔧 Prompt工程技巧：**
1. **角色扮演**："你是一个资深的Python架构师..."
2. **分步指导**："第一步...第二步...第三步..."
3. **Few-shot示例**：提供2-3个示例让AI理解模式
4. **思维链**："让我们一步步思考..."
5. **格式约束**："用Markdown表格输出结果"

---

### 4️⃣ Rules - 规则/代码规范

**💡 是什么？**
- 给AI设定的行为规范和代码标准
- 在Cursor中是`.cursorrules`文件
- 让AI自动遵循团队的编码规范

**🎯 能做什么？**
- ✅ 统一团队代码风格
- ✅ 自动应用最佳实践
- ✅ 强制类型安全
- ✅ 禁止不安全的代码模式
- ✅ 自定义命名规范

**📌 实际应用：**

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

**效果：**
```typescript
// AI会自动生成符合规则的代码

// ✅ 符合规则
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

// ❌ AI不会生成违反规则的代码
function getUser(id, callback) {  // 违反：没类型、用回调
  db.query("SELECT * FROM users WHERE id=" + id, callback);  // 违反：SQL注入风险
}
```

---

## 🚀 【快速导航】

### 👤 按角色选择

| 角色 | 推荐工具 | 直达链接 |
|-----|---------|---------|
| 👶 完全小白 | Kimi（免费） | [跳转](#小白工具) |
| 👨‍💻 程序员 | Cursor + Claude 4 | [跳转](#编程工具) |
| 🎨 UI设计师 | v0.dev + Stitch | [跳转](#UI生成) |
| 👨‍💼 产品经理 | ChatGPT + Notion AI | [跳转](#产品工具) |
| 🎬 视频/设计 | Sora 2 + 剪映 | [跳转](#设计工具) |

---

## 📊 【工具对比总览】

<div id="编程工具"></div>

### 🖥️ 编程开发工具（程序员必备）

#### 1. Cursor - AI原生代码编辑器 ⭐⭐⭐⭐⭐

**💡 主要特点：**
- 基于VS Code深度定制，AI功能原生集成
- 支持多模型切换（Claude 4、GPT-4o、Gemini 2.5等）
- `Ctrl+K` 内联编辑，`Ctrl+L` 对话式编程
- `@符号` 引用文件/文件夹上下文
- **Background Agent** 自动化处理复杂任务

**🤖 MCP支持：**
- ✅ 通过MCP服务器连接外部数据源
- ✅ 读取本地文件系统
- ✅ 连接数据库和API
- 配置方式：在设置中添加MCP服务器配置

**🎯 AI Agent能力：**
- **Background Agent模式**：并行处理多个任务
  - 示例："帮我重构整个项目使用TypeScript"
  - Agent会：扫描文件 → 逐个转换 → 修复类型错误 → 更新配置
- **自动化PR生成**：从Issue描述自动实现功能并提交PR
- **跨文件重构**：智能理解依赖关系，批量修改

**✍️ Prompt最佳实践：**
```
❌ 差的："优化这段代码"

✅ 好的："重构这个函数，要求：
1. 使用async/await替代Promise.then
2. 添加完整的错误处理
3. 优化数据库查询，减少N+1问题
4. 添加TypeScript类型注解
5. 保持原有功能不变"
```

**📋 Rules配置：**
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

**🎯 适用任务：**
- ✅ 快速理解陌生代码库（@folders整个项目）
- ✅ 实时代码补全和生成
- ✅ 大规模代码重构
- ✅ Bug定位和修复
- ✅ 代码审查和安全检查
- ✅ 自动化测试生成

**💰 收费情况：**
- **免费版**：基础代码补全，有使用次数限制
- **Pro版**：$20/月，无限使用所有模型，优先响应，支持Background Agent
- **Team版**：$40/月/人，团队协作 + 代码库索引 + 共享Rules

**🌐 访问方式：**
- 官网：https://cursor.so
- 支持平台：Windows / macOS / Linux
- 下载后直接安装，可导入VS Code配置

**📌 高级使用技巧：**
1. **使用@符号精准引用**：
   - `@filename.ts` - 引用单个文件
   - `@folders src/` - 引用整个目录
   - `@docs README.md` - 引用文档

2. **组合使用Ctrl+K和Ctrl+L**：
   - Ctrl+K：快速局部修改
   - Ctrl+L：复杂问题讨论和方案设计

3. **Background Agent工作流**：
   ```
   1. 创建详细的任务描述
   2. 启动Background Agent
   3. Agent自动分解任务并执行
   4. 实时查看进度
   5. Review并合并修改
   ```

---

#### 2. Claude 4 Sonnet - 最强编程AI ⭐⭐⭐⭐⭐

**💡 主要特点：**
- Anthropic 2025最新模型，编程能力业界最强
- **200K tokens** 超长上下文（约15万字代码）
- 支持多模态（代码、文档、图表、PDF、图片）
- **思维链推理**：展示思考过程
- **Projects功能**：管理长期项目知识库

**🤖 MCP支持：**
- ✅ **原生支持MCP**（Anthropic自己开发的协议）
- ✅ Claude Desktop可配置MCP服务器
- ✅ 连接文件系统、数据库、API
- 配置文件位置：
  - macOS: `~/Library/Application Support/Claude/claude_desktop_config.json`
  - Windows: `%APPDATA%\Claude\claude_desktop_config.json`

**MCP配置示例：**
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

**🎯 AI Agent能力：**
- **多步骤推理**：自动分解复杂任务
- **工具调用**：通过MCP调用外部工具
- **自我纠错**：发现错误自动修正
- 示例：
  ```
  你："帮我创建一个完整的用户认证系统"
  
  Claude Agent会：
  1. 设计数据库schema
  2. 生成Prisma模型
  3. 实现JWT认证逻辑
  4. 创建注册/登录API
  5. 添加密码加密
  6. 编写单元测试
  7. 生成API文档
  ```

**✍️ Prompt工程：**

**Claude特别擅长的Prompt模式：**

1. **XML标签结构化**：
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

2. **角色+思维链**：
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

3. **Few-shot示例**：
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

**📋 Projects功能（相当于持久化Rules）：**
- 创建Project存储项目知识
- 包含：代码规范、架构文档、API文档
- Claude会记住Project中的所有信息
- 适合长期维护的项目

**Project示例结构：**
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

**🎯 适用任务：**
- ✅ 代码深度审查（性能、安全、可维护性）
- ✅ 系统架构设计和技术选型
- ✅ 大规模代码重构（处理整个代码库）
- ✅ 复杂Bug深度诊断
- ✅ API文档和技术文档生成
- ✅ 代码学习和教学（解释复杂概念）
- ✅ 算法设计和优化

**💰 收费情况：**
- **免费版**：约50次对话/天，使用Claude 4 Sonnet
- **Pro版**：$20/月，5倍使用量，支持所有模型，包含Projects功能
- **API版**：按Token计费，$3输入/$15输出（每百万tokens）

**🌐 访问方式：**
- 网页版：https://claude.ai
- Claude Desktop：https://claude.ai/download
- API文档：https://docs.anthropic.com

**📌 高级使用技巧：**

1. **超长上下文利用**：
   - 一次性粘贴整个代码库（200K tokens ≈ 约30个文件）
   - 上传完整技术文档PDF
   - 让Claude理解整个项目后再提问

2. **多模态应用**：
   - 上传架构图让Claude分析设计
   - 上传错误截图让Claude诊断
   - 上传数据库ER图让Claude生成Schema

3. **MCP实战**：
   ```
   配置MCP后：
   "读取我的GitHub仓库所有Issue"
   "分析我项目的数据库结构"
   "查看我最近的Git提交"
   ```

---

#### 3. GitHub Copilot - 实时代码补全 ⭐⭐⭐⭐

**💡 主要特点：**
- OpenAI Codex驱动，实时代码建议
- 深度GitHub集成，理解数百万开源项目模式
- 支持30+主流IDE
- 支持80+编程语言
- **Copilot Chat**：在IDE内对话式编程

**🤖 MCP支持：**
- ❌ 不直接支持MCP
- ✅ 通过GitHub生态间接访问仓库数据

**🎯 AI Agent能力：**
- **Copilot Workspace**（新功能）：
  - 基于GitHub Issue自动生成PR
  - 自动规划实现步骤
  - 跨文件修改和测试
- **多文件编辑**：理解项目上下文，修改相关文件

**✍️ Prompt技巧（通过注释）：**

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

**📋 Rules配置：**
- 通过 `.gitattributes` 和注释引导
- 在项目根目录创建 `CONVENTIONS.md`
- Copilot会学习项目风格

**🎯 适用任务：**
- ✅ 快速编写样板代码（CRUD、API调用）
- ✅ 根据注释自动实现函数
- ✅ 自动生成单元测试
- ✅ 学习新技术和API用法
- ✅ 代码片段快速生成
- ✅ 重复代码模式识别

**💰 收费情况：**
- **个人版**：$10/月
- **企业版**：$19/月/人，支持代码隐私保护
- **学生/教师**：✅ 免费（需GitHub Education认证）
- **开源维护者**：✅ 免费（需认证）

**🌐 访问方式：**
- 订阅：https://github.com/features/copilot
- 支持IDE：VS Code、IntelliJ IDEA、PyCharm、Neovim、Visual Studio
- 安装：在IDE扩展商店搜索"GitHub Copilot"

**📌 高级使用技巧：**

1. **多行补全**：
   - 按 `Tab` 接受建议
   - 按 `Alt+]` 查看下一个建议
   - 按 `Ctrl+Enter` 查看多个建议

2. **Copilot Chat使用**：
   ```
   /explain - 解释选中代码
   /fix - 修复bug
   /tests - 生成测试
   /doc - 生成文档
   ```

3. **上下文优化**：
   - 打开相关文件让Copilot学习项目风格
   - 在注释中提供详细需求

---

#### 4. Gemini 2.5 Pro - Google多模态AI ⭐⭐⭐⭐

**💡 主要特点：**
- Google 2025最新模型
- **200万tokens** 超长上下文（业界最长，约150万字）
- 强大多模态能力（文本、图片、视频、音频、代码）
- 深度集成Google生态（Gmail、Drive、Docs、Colab）
- 实时联网搜索

**🤖 MCP支持：**
- ❌ 不支持MCP协议
- ✅ 通过Google API访问Google服务
- ✅ Gemini Extensions连接Gmail、Drive等

**🎯 AI Agent能力：**
- **多模态推理**：同时处理代码、图片、文档
- **工具调用**：通过Extensions调用Google服务
- **代码执行**：在Google Colab中执行Python代码
- 示例：
  ```
  你："分析我Drive里的项目代码和架构图，给出优化建议"
  
  Gemini会：
  1. 读取Drive中的代码文件
  2. 分析架构图图片
  3. 理解项目结构
  4. 提供详细优化方案
  5. 生成改进后的代码
  ```

**✍️ Prompt最佳实践：**

**利用超长上下文：**
```
我要上传我整个项目的代码（50个文件，约100万字）

[上传所有文件]

现在请：
1. 分析整体架构设计
2. 找出所有潜在bug
3. 检查安全漏洞
4. 提供性能优化建议
5. 生成完整的重构方案
```

**多模态Prompt：**
```
[上传：代码文件 + 架构图 + 需求文档PDF + 数据库ER图]

请基于这些材料：
1. 验证代码是否符合架构设计
2. 检查是否满足需求文档
3. 优化数据库设计
4. 提供改进建议
```

**📋 Rules配置：**
- 在对话开始时设定规则
- 使用System Instruction（类似.cursorrules）

**System Instruction示例：**
```
你是一个Google Cloud架构专家。

代码规范：
- 使用Python 3.11+
- 遵循Google Python Style Guide
- 使用type hints
- 文档字符串使用Google风格

架构偏好：
- 优先使用Google Cloud服务
- 使用Cloud Run部署
- 数据库用Cloud SQL
- 缓存用Memorystore

安全要求：
- 所有API使用IAM认证
- 敏感数据加密
- 遵循最小权限原则
```

**🎯 适用任务：**
- ✅ 超大型项目分析（整个代码库）
- ✅ 技术文档PDF快速提取信息（上传几百页文档）
- ✅ 架构图分析和优化建议
- ✅ 多文件代码审查
- ✅ 视频教程内容提取和代码实现
- ✅ 跨语言代码转换
- ✅ Google Cloud项目开发

**💰 收费情况：**
- **免费版**：Gemini 2.0 Flash，有使用限制
- **Gemini Advanced**：$19.99/月，Gemini 2.5 Pro，2TB Google One存储
- **API版**：$1.25输入/$5输出（每百万tokens）

**🌐 访问方式：**
- 网页版：https://gemini.google.com
- Google Colab集成：https://colab.google
- API文档：https://ai.google.dev/docs

**📌 高级使用技巧：**

1. **超长上下文策略**：
   ```
   第一次对话：上传所有项目代码
   后续对话：Gemini已记住所有代码，直接提问
   
   "找出所有API接口"
   "分析数据库查询性能"
   "生成项目文档"
   ```

2. **多模态组合**：
   - 上传设计稿 + 代码，验证实现一致性
   - 上传错误日志截图，快速定位问题
   - 上传技术视频，提取代码和知识点

3. **Google生态集成**：
   ```
   "读取我Gmail中的bug报告"
   "分析Drive中的需求文档"
   "在Colab中运行这段代码"
   ```

---

#### 5. Grok 4 - xAI最新模型 ⭐⭐⭐

**💡 主要特点：**
- Elon Musk的xAI团队开发
- 与X平台（Twitter）深度集成
- **实时联网**，获取最新技术动态
- 回答风格幽默、不枯燥
- Grok 4性能大幅提升

**🤖 MCP支持：**
- ❌ 不支持MCP

**🎯 AI Agent能力：**
- **实时信息检索**：搜索X平台最新技术讨论
- **趋势分析**：追踪技术社区动态
- 适合了解新技术和最佳实践

**✍️ Prompt建议：**
```
// 利用Grok的实时能力
"最近一周AI编程工具有什么重大更新？"
"React 19正式版发布了吗？有哪些新特性？"
"开发者社区对Rust的看法如何？"
```

**📋 Rules配置：**
- 在对话开始时设定

**🎯 适用任务：**
- ✅ 了解最新技术趋势和新闻
- ✅ 代码生成和调试
- ✅ 技术问题解答
- ✅ 创意编程方案
- ✅ 技术社区观点获取

**💰 收费情况：**
- **需要X Premium+订阅**：$16/月（包含X平台所有Premium功能）

**🌐 访问方式：**
- 方式1：https://x.com - 登录后侧边栏找到Grok
- 方式2：https://grok.x.ai
- 需要X Premium+会员

---

<div id="UI生成"></div>

### 🎨 UI代码生成工具（前端开发神器）

#### 1. v0.dev - Vercel官方UI生成器 ⭐⭐⭐⭐⭐

**💡 主要特点：**
- Vercel官方出品，专注前端UI生成
- 生成高质量React/Next.js/TypeScript代码
- 支持Tailwind CSS、shadcn/ui组件库
- 实时预览，一键复制代码
- 生成的代码可直接用于生产环境

**🎯 AI Agent能力：**
- 理解设计稿自动生成代码
- 支持迭代优化
- 自动处理响应式布局

**✍️ Prompt技巧：**
```
❌ 差的："做个登录页面"

✅ 好的："创建一个现代风格的登录页面
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

**🎯 适用任务：**
- ✅ 快速搭建页面UI界面
- ✅ 生成React组件代码
- ✅ 创建表单、卡片、导航等组件
- ✅ 快速原型开发
- ✅ 学习React和Tailwind最佳实践

**💰 收费情况：**
- **免费版**：200积分/月（约20-30个组件）
- **付费版**：$20/月，5000积分/月
- 每次生成消耗约10积分

**🌐 访问方式：**
- 官网：https://v0.dev
- 需要Vercel账号（GitHub登录即可）
- 网页直接使用，无需安装

---

#### 2. Stitch - Google设计转代码工具 ⭐⭐⭐⭐⭐

**💡 主要特点：**
- Google官方出品，Figma到代码的桥梁
- AI理解设计稿，生成高质量代码
- 支持React、Vue、Angular
- Material Design风格原生支持
- 保持设计和代码同步

**🎯 AI Agent能力：**
- 自动识别设计组件
- 智能生成响应式代码
- 理解设计规范自动应用

**✍️ 使用流程：**
```
1. 在Figma中设计UI
2. 使用Stitch插件
3. 选择要导出的组件
4. AI自动生成代码
5. 一键复制到项目中
```

**🎯 适用任务：**
- ✅ Figma设计稿转代码
- ✅ 设计系统实现
- ✅ UI组件库开发
- ✅ 保持设计与代码一致

**💰 收费情况：**
- **免费版**：基础功能
- **Pro版**：定价见官网

**🌐 访问方式：**
- 官网：https://stitch.withgoogle.com
- Figma插件商店搜索"Stitch"

---

#### 3. bolt.new - StackBlitz全栈应用生成 ⭐⭐⭐⭐⭐

**💡 主要特点：**
- StackBlitz出品，生成完整Web应用
- 支持React、Vue、Node.js等技术栈
- 在线IDE环境，实时运行预览
- 持续对话修改完善
- 支持导出项目代码

**🎯 AI Agent能力：**
- 自动生成完整项目结构
- 前后端同时生成
- 自动配置依赖和构建工具

**✍️ Prompt示例：**
```
"创建一个任务管理Web应用：

前端：
- React + TypeScript + Vite
- Tailwind CSS样式
- 用户可以添加、编辑、删除任务
- 任务有状态：待办、进行中、已完成
- 支持拖拽排序
- 本地存储用localStorage

后端（可选）：
- Node.js + Express
- SQLite数据库
- RESTful API
- JWT认证

请生成完整可运行的项目"
```

**🎯 适用任务：**
- ✅ 生成完整的全栈应用
- ✅ 快速搭建项目骨架
- ✅ 创建Landing Page
- ✅ 构建管理后台
- ✅ 教学演示和原型验证

**💰 收费情况：**
- **免费版**：有使用次数限制
- **付费版**：$20/月，无限使用

**🌐 访问方式：**
- 官网：https://bolt.new
- 浏览器直接使用

---

#### 4. Lovable (GPT Engineer) - AI全栈开发 ⭐⭐⭐⭐

**💡 主要特点：**
- 从自然语言描述生成完整应用
- 支持React、Next.js、Supabase
- 自动部署到云端
- 可视化编辑界面

**✍️ Prompt示例：**
```
"创建一个SaaS订阅管理系统：

功能：
1. 用户注册和登录
2. 订阅套餐选择（月付/年付）
3. Stripe支付集成
4. 用户仪表板（使用情况、账单）
5. 管理后台（用户管理、数据统计）

技术栈：
- Next.js 14
- Supabase（数据库和认证）
- Stripe（支付）
- Tailwind CSS
- TypeScript

请生成完整项目并部署"
```

**🎯 适用任务：**
- ✅ 快速构建MVP产品
- ✅ 创建SaaS应用原型
- ✅ 全栈项目搭建

**💰 收费情况：**
- **Hobby版**：$29/月
- **Pro版**：$99/月

**🌐 访问方式：**
- 官网：https://lovable.dev

---

#### 5. Replit Agent - 在线AI协作开发 ⭐⭐⭐⭐

**💡 主要特点：**
- 在线IDE + AI编程助手
- 支持50+编程语言
- 实时协作，多人同时编辑
- 内置部署功能

**🎯 AI Agent能力：**
- 自动配置开发环境
- 智能安装依赖
- 一键部署到生产

**✍️ 使用方式：**
```
在Replit中问AI：
"创建一个Express API服务器，有用户CRUD接口"
"添加JWT认证"
"部署到生产环境"
```

**🎯 适用任务：**
- ✅ 在线协作开发
- ✅ 编程教学和学习
- ✅ 快速验证想法
- ✅ API开发和测试

**💰 收费情况：**
- **免费版**：有资源限制
- **Core版**：$7/月

**🌐 访问方式：**
- 官网：https://replit.com

---

<div id="小白工具"></div>

### 👶 小白/通用AI工具（推荐从这里开始）

#### 1. Kimi - 月之暗面超长上下文AI ⭐⭐⭐⭐⭐

**💡 主要特点：**
- 国产AI，月之暗面（Moonshot AI）出品
- **200万字**超长上下文（约4本《红楼梦》）
- 可以一次性读完整本书、长论文
- 中文理解能力极强
- **完全免费**，无使用限制

**🎯 适用任务：**
- ✅ 长文档阅读和总结（论文、报告、合同）
- ✅ 学习资料整理（上传PDF、Word）
- ✅ 日常聊天问答
- ✅ 写作辅助（文章、报告、总结）
- ✅ 翻译（中英互译）
- ✅ 代码解释和学习

**💰 收费情况：**
- ✅ **完全免费**，无任何限制！

**🌐 访问方式：**
- 官网：https://kimi.moonshot.cn
- 无需科学上网
- 支持手机号/微信登录

---

#### 2. 通义千问 - 阿里云多模态AI ⭐⭐⭐⭐⭐

**💡 主要特点：**
- 阿里云出品
- 支持多模态（文字、图片、文档）
- 深度集成阿里生态

**🎯 适用任务：**
- ✅ 办公文档处理
- ✅ 图片理解和分析
- ✅ 代码辅助

**💰 收费情况：**
- **免费版**：功能完整
- **Plus版**：¥60/月

**🌐 访问方式：**
- 官网：https://tongyi.aliyun.com

---

#### 3. 豆包 - 字节跳动AI助手 ⭐⭐⭐⭐

**💡 主要特点：**
- 字节跳动出品
- 完全免费，无限制
- 响应速度快

**🎯 适用任务：**
- ✅ 日常聊天
- ✅ 写作辅助
- ✅ 知识问答

**💰 收费情况：**
- ✅ **完全免费**

**🌐 访问方式：**
- 官网：https://doubao.com

---

<div id="设计工具"></div>

### 🎨 设计/图像/视频工具

#### 1. Sora 2 - OpenAI视频生成 ⭐⭐⭐⭐⭐

**💡 主要特点：**
- OpenAI 2025最新视频生成模型
- 从文字描述生成高质量视频
- 支持最长60秒视频
- 物理规律准确，运动流畅
- 支持多种视频风格

**🎯 适用任务：**
- ✅ 文字生成视频
- ✅ 产品宣传片
- ✅ 教学演示视频
- ✅ 创意视频制作
- ✅ 概念验证

**✍️ Prompt示例：**
```
"创建一个30秒的产品宣传视频：

场景：现代化办公室
镜头：从窗外推进，展示团队在使用我们的软件
风格：商业广告风格，明亮温暖色调
音乐：轻快的背景音乐
文字：产品名称和Slogan
分辨率：1920x1080"
```

**💰 收费情况：**
- 定价待官方公布
- 预计包含在ChatGPT Pro订阅中

**🌐 访问方式：**
- 官网：https://openai.com/sora
- 需要等待正式发布

---

#### 2. 剪映 - 视频剪辑AI工具 ⭐⭐⭐⭐⭐

**💡 主要特点：**
- 字节跳动出品
- **自动识别语音生成字幕**
- 智能剪辑，一键成片
- **完全免费**

**🎯 适用任务：**
- ✅ 短视频制作
- ✅ Vlog剪辑
- ✅ 会议录屏加字幕
- ✅ 自动去水印

**💰 收费情况：**
- ✅ **完全免费**

**🌐 访问方式：**
- 搜索"剪映"下载APP
- 支持Windows、macOS、iOS、Android

---

#### 3. Canva - 零基础设计工具 ⭐⭐⭐⭐⭐

**💡 主要特点：**
- 零基础也能做设计
- 海量模板
- AI辅助设计

**🎯 适用任务：**
- ✅ PPT制作
- ✅ 海报设计
- ✅ 社交媒体内容

**💰 收费情况：**
- **免费版**：够用
- **Pro版**：$12.99/月

**🌐 访问方式：**
- 官网：https://www.canva.com

---

## 💰 【价格汇总】

| 价格 | 工具 |
|-----|------|
| **✅ 完全免费** | Kimi、豆包、剪映、通义千问免费版 |
| **$10/月** | GitHub Copilot |
| **$20/月** | Cursor Pro、Claude Pro、ChatGPT Plus、Gemini Advanced、v0.dev、bolt.new |
| **$29+/月** | Lovable、Midjourney Pro |

---

## 📚 【学习资源】

- [Cursor文档](https://docs.cursor.sh)
- [Claude MCP文档](https://docs.anthropic.com/mcp)
- [Prompt工程指南](https://www.promptingguide.ai)

---

**最后更新：2025年10月4日**