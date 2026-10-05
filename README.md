# Trace Math Solution

一个用于生成详细、可复现数学证明与多步推导的 Codex Skill。

它强调保留真实的探索过程：先从题目结构和常见方法出发形成候选路线，明确其中尚未证明的地方，再在正式解答中逐项完成证明义务。每个关键步骤都会说明本步目标、方法选择、完整推导和本步结论。

## 适用场景

当用户明确提出以下要求时启用：

- 详细证明；
- 完整推导；
- 不省略步骤；
- 展示可复现的解题思路；
- 或直接调用 `$trace-math-solution`。

普通求解、只要答案、简短提示或常规计算不会自动触发。

## 主要特点

- 解答开头列出将使用的知识点，并根据对话与可访问的学习资料判断掌握情况。
- 分析阶段允许使用直觉和暂时不严谨的候选方法，但会明确暴露逻辑缺口。
- 正式解答逐步验证分析阶段提出的证明义务。
- 不用“整理可得”“同理可得”等表述隐藏实质推导。
- 对尚未确认掌握的重要工具提供补充解释。
- 附带正面范例，用于校准分析深度、探索痕迹和书写格式。

## 文件结构

```text
trace-math-solution/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── answer-pattern.md
    └── oscillating-recurrence-example.md
```

## 安装

可以让 Codex 的 `$skill-installer` 从本 GitHub 仓库安装，也可以把仓库内容复制到个人 Skills 目录下的 `trace-math-solution` 文件夹。

安装后，直接提出“请详细证明”“请给出完整推导”等要求即可按描述自动触发；也可以显式输入 `$trace-math-solution`。

## 范例

- `references/answer-pattern.md`：由用户手写证明改良得到的递推数列正面范例。
- `references/oscillating-recurrence-example.md`：展示如何从原数列震荡转向奇偶子列与二步递推。
