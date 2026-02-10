# 代码审查专家

一个面向 AI 代理的全面代码审查技能。以资深工程师的视角执行结构化审查，涵盖架构、安全、性能和代码质量。

## 安装

```bash
npx skills add sanyuan0704/code-review-expert
```

## 特性

- **SOLID 原则** - 检测 SRP、OCP、LSP、ISP、DIP 违规
- **安全扫描** - XSS、注入、SSRF、竞态条件、认证漏洞、密钥泄露
- **性能** - N+1 查询、CPU 热点、缺失缓存、内存问题
- **错误处理** - 吞咽异常、异步错误、缺失边界
- **边界条件** - 空值处理、空集合、差一错误、数值限制
- **删除规划** - 识别死代码并提供安全删除计划

## 使用

安装后，只需运行：

```
/code-review-expert
```

该技能将自动审查您当前的 git 更改。

## 工作流程

1. **预检** - 通过 `git diff` 确定更改范围
2. **SOLID + 架构** - 检查设计原则
3. **删除候选** - 查找死代码/未使用代码
4. **安全扫描** - 漏洞检测
5. **代码质量** - 错误处理、性能、边界条件
6. **输出** - 按严重性分类的发现（P0-P3）
7. **确认** - 在实施修复前询问用户

## 严重性级别

| 级别 | 名称 | 操作 |
|-------|------|--------|
| P0 | 严重 | 必须阻止合并 |
| P1 | 高 | 应在合并前修复 |
| P2 | 中 | 修复或创建后续任务 |
| P3 | 低 | 可选改进 |

## 结构

```
code-review-expert/
├── SKILL.md                 # 主要技能定义
├── agents/
│   └── agent.yaml           # 代理接口配置
└── references/
    ├── solid-checklist.md   # SOLID 异味提示
    ├── security-checklist.md    # 安全与可靠性
    ├── code-quality-checklist.md # 错误、性能、边界
    └── removal-plan.md      # 删除规划模板
```

## 参考资料

每个检查清单都提供详细的提示和反模式：

- **solid-checklist.md** - SOLID 违规 + 常见代码异味
- **security-checklist.md** - OWASP 风险、竞态条件、加密、供应链
- **code-quality-checklist.md** - 错误处理、缓存、N+1、空值安全
- **removal-plan.md** - 安全删除 vs 延迟删除与回滚计划

## 许可证

MIT
