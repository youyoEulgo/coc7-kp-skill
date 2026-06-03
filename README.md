# COC7-KP-Skill

《克苏鲁的呼唤》7版 — Claude Code KP助理 Skill

## 这是什么

一个 **Claude Code Skill**，让KP带COC团变得格外轻松。

你只需要像平时一样描述场景、告诉助理玩家做了什么。助理会自动处理角色演绎、数值计算、规则查询和日志记录——你可以专注于推进剧情和扮演NPC，不再需要一边带团一边翻规则书。

## 安装

```bash
# 在你的COC项目目录下
cd your-coc-project
mkdir -p .claude/skills
git clone https://github.com/youyoEulgo/coc7-kp-skill.git .claude/skills/kp-assistant
```

### 设置自动加载（可选）

在项目目录下的 `.claude/settings.json`（不是 `~/.claude/`）中添加：

```bash
# settings.json 的位置是：
# your-coc-project/.claude/settings.json
```

```json
{
  "skills": {
    "autoLoad": ["kp-assistant"]
  }
}
```

配置后每次在这个项目目录下打开新对话，skill会自动生效。

如果不配置自动加载，每次对话中输入 `/kp-assistant` 手动激活也可以。

## 用法

配置后正常带团即可，助理会在后台自动工作：

- KP描述场景 → 助理补充氛围细节，提示需要的检定
- PL做出行动 → 助理判断对应技能、设置难度、指示投骰
- 投完骰子 → 助理判定结果、推进演绎、记录log
- 需要查规则 → 直接问，助理翻规则文件给出答案

骰子支持两种模式：

| 模式 | 说明 |
|:----|:------|
| **真实骰子**（默认） | 助理发指令，KP自己投，投完告诉助理判定 |
| **自动骰子** | 告诉助理"自动骰"，由助理用bash工具roll骰判定 |

日志在游戏过程中自动累积记录，保存到项目 `log/` 目录下。

## 结构

```
.claude/skills/kp-assistant/
├── SKILL.md              # 主skill：角色定义 + 核心流程 + 规则速查
└── references/           # 规则参考文件
    ├── official/         # 规则书原文（15个文件）
    │   ├── skill-core-mechanics.md    # 三级难度、孤注一骰、奖励骰
    │   ├── skill-skills.md            # 48个技能定义
    │   ├── skill-sanity.md            # 理智系统
    │   ├── skill-battle.md            # 战斗流程
    │   └── ...
    └── custom/
        ├── general/      # 通用自定义规则
        │   ├── skill-diaomin.md       # 刁民行为处理
        │   ├── skill-kp-assist.md     # KP助理工作流程
        │   └── skill-log-format.md    # log格式规范
        └── module-*/     # 各模组专用数据（按需创建）
```

## 自定义

每个模组有特有数据时，在 `references/custom/` 下建 `module-<模组名>/` 目录即可，通用部分不受影响。

## 前提

建议搭配完整规则书文本（`core_rules.txt`）使用，可获得更精确的规则查询能力。skill自带的规则摘要覆盖了核心内容，但完整规则书可以提供更详细的上下文。

## 协议

MIT
