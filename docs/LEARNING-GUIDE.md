# Everything Claude Code 学习指南

本指南帮助你系统地学习和掌握 Everything Claude Code (ECC) 项目。

## 📋 项目概览

ECC 是一个生产级的 AI 编码插件系统，包含：

- **30 个 Agents** - 专门的子代理处理特定任务
- **136 个 Skills** - 工作流定义和领域知识
- **60 个 Commands** - 用户可调用的斜杠命令
- **Hooks** - 自动化触发器
- **Rules** - 编码规范和最佳实践
- **MCP Configs** - Model Context Protocol 服务器配置

## 🎯 学习路径

### 第一阶段：基础理解（1-2天）

**目标：** 理解项目结构和核心概念

#### 必读文档

1. `README.md` - 项目概览和快速开始
2. `AGENTS.md` - Agent 系统说明
3. `CONTRIBUTING.md` - 贡献指南和开发规范
4. `examples/CLAUDE.md` - 配置示例

#### 理解目录结构

```
everything-claude-code/
├── agents/          # 专门的子代理
├── skills/          # 工作流技能
├── commands/        # 斜杠命令
├── hooks/           # 自动化钩子
├── rules/           # 编码规范
├── scripts/         # 工具脚本
├── mcp-configs/     # MCP服务器配置
└── tests/           # 测试套件
```

#### 实践任务

```bash
# 1. 安装依赖
npm install

# 2. 运行测试
npm test

# 3. 查看项目结构
ls -la agents/ skills/ commands/
```

### 第二阶段：核心组件（3-5天）

**目标：** 深入理解各个组件的工作原理

#### 学习 Commands

Commands 是用户直接调用的入口点。

**推荐阅读顺序：**

1. `commands/tdd.md` - 测试驱动开发
2. `commands/code-review.md` - 代码审查
3. `commands/plan.md` - 实施计划

**实践：** 尝试在 Claude Code 中运行这些命令

#### 学习 Skills

Skills 定义了工作流和最佳实践。

**推荐阅读顺序：**

1. `skills/tdd-workflow/SKILL.md` - TDD 工作流
2. `skills/systematic-debugging/SKILL.md` - 系统化调试
3. `skills/code-review/SKILL.md` - 代码审查流程

**关键概念：**
- When to Use - 何时使用这个技能
- How It Works - 工作原理
- Examples - 实际示例

#### 学习 Agents

Agents 是专门处理特定任务的子代理。

**推荐阅读顺序：**

1. `agents/code-reviewer.md` - 代码审查专家
2. `agents/build-error-resolver.md` - 构建错误解决
3. `agents/architect.md` - 架构设计

**Agent 结构：**
```yaml
---
name: agent-name
description: 简短描述
tools: ["Read", "Grep", "Bash"]
model: sonnet
---
# Agent 的详细指令
```

#### 学习 Hooks

Hooks 在特定事件触发时自动执行。

**推荐阅读：**

1. `hooks/hooks.json` - Hook 配置
2. `scripts/hooks/session-start.js` - 会话开始钩子
3. `scripts/hooks/post-edit-format.js` - 编辑后格式化

**Hook 类型：**
- `SessionStart` - 会话开始
- `PreToolUse` - 工具使用前
- `PostToolUse` - 工具使用后
- `SessionEnd` - 会话结束

### 第三阶段：深入实践（1-2周）

**目标：** 动手修改和扩展项目

#### 任务 1：创建自定义 Skill

```bash
# 1. 创建目录
mkdir -p skills/my-skill

# 2. 创建 SKILL.md
cat > skills/my-skill/SKILL.md << 'EOF'
---
name: my-skill
description: 我的自定义技能
---

## When to Use

描述何时使用这个技能

## How It Works

描述工作原理

## Examples

提供示例
EOF
```

#### 任务 2：添加语言规则

为你常用的编程语言添加规则：

```bash
# 创建语言规则目录
mkdir -p rules/my-language

# 添加规则文件
touch rules/my-language/coding-style.md
touch rules/my-language/testing.md
touch rules/my-language/security.md
```

#### 任务 3：编写自定义 Hook

创建一个简单的 hook：

```javascript
// scripts/hooks/my-hook.js
module.exports = async function run(input) {
  // 处理输入
  console.log('Hook triggered:', input);
  
  // 返回结果
  return { success: true };
};
```

#### 任务 4：理解测试系统

```bash
# 运行所有测试
npm test

# 运行特定测试
node tests/lib/utils.test.js

# 查看测试覆盖率
npm run coverage
```

### 第四阶段：高级主题（持续学习）

**目标：** 掌握高级特性和最佳实践

#### 高级 Skills

1. `skills/multi-agent-orchestration/SKILL.md` - 多代理编排
2. `skills/continuous-learning/SKILL.md` - 持续学习
3. `skills/security-review/SKILL.md` - 安全审查

#### MCP 集成

学习如何配置和使用 MCP 服务器：

1. `mcp-configs/README.md` - MCP 配置指南
2. 查看示例配置文件
3. 创建自定义 MCP 服务器

#### 贡献代码

1. Fork 项目
2. 创建功能分支
3. 遵循 `CONTRIBUTING.md` 中的规范
4. 提交 Pull Request

## 📚 推荐阅读顺序

### 第 1 天：基础
- [ ] README.md
- [ ] AGENTS.md
- [ ] examples/CLAUDE.md

### 第 2-3 天：核心组件
- [ ] agents/code-reviewer.md
- [ ] skills/tdd-workflow/SKILL.md
- [ ] commands/tdd.md
- [ ] hooks/hooks.json

### 第 4-5 天：深入学习
- [ ] scripts/hooks/session-start.js
- [ ] tests/run-all.js
- [ ] rules/common/javascript.md

### 第 6-7 天：高级主题
- [ ] skills/systematic-debugging/SKILL.md
- [ ] agents/architect.md
- [ ] mcp-configs/README.md

## 💡 学习技巧

1. **边学边做** - 不要只看代码，实际运行和修改
2. **从简单开始** - 先理解简单的 agent 和 skill
3. **理解模式** - 注意重复出现的模式和约定
4. **运行测试** - 测试是最好的文档
5. **提问和讨论** - 在 GitHub issues 或社区提问
6. **记录笔记** - 记录你的学习过程和发现

## 🎓 学习检查点

完成每个阶段后，确保你能回答以下问题：

### 阶段 1 检查点
- [ ] 我能解释 ECC 的主要组件是什么吗？
- [ ] 我理解项目的目录结构吗？
- [ ] 我能成功运行测试吗？

### 阶段 2 检查点
- [ ] 我能解释 Command、Skill 和 Agent 的区别吗？
- [ ] 我理解 Hook 的触发机制吗？
- [ ] 我能阅读和理解现有的 agent 代码吗？

### 阶段 3 检查点
- [ ] 我能创建自己的 skill 吗？
- [ ] 我能为新语言添加 rules 吗？
- [ ] 我能编写和测试自定义 hook 吗？

### 阶段 4 检查点
- [ ] 我能贡献代码到项目吗？
- [ ] 我理解 MCP 集成吗？
- [ ] 我能设计和实现复杂的工作流吗？

## 🔗 相关资源

- [GitHub Repository](https://github.com/affaan-m/everything-claude-code)
- [Issues](https://github.com/affaan-m/everything-claude-code/issues)
- [Discussions](https://github.com/affaan-m/everything-claude-code/discussions)
- [Claude Code Documentation](https://docs.anthropic.com/claude/docs)

## 🤝 获取帮助

遇到问题？

1. 查看 `docs/` 目录中的文档
2. 搜索 GitHub Issues
3. 在 Discussions 中提问
4. 查看测试文件了解用法示例

---

**祝学习愉快！** 🚀
