# COC7-KP-Skill

《克苏鲁的呼唤》7版 — Claude Code KP助理 Skill

## 这是什么

一个 **Claude Code Skill**，让你在跑COC 7版团时拥有一个KP助理。它会帮你：

- 📝 **记录log** — 叙事风格的跑团日志
- 🎲 **指示投骰** — 告诉你投什么骰子，你投它判
- 🧮 **计算数值** — 伤害、SAN、奖励骰/惩罚骰
- 📖 **查阅规则** — 规则书全文索引，随查随到

## 安装

```bash
# 在你的COC项目目录下
cd your-coc-project
mkdir -p .claude/skills
git clone https://github.com/youyoEulgo/coc7-kp-skill.git .claude/skills/kp-assistant
```

然后在对话中使用 `/kp-assistant` 激活，或设置为自动加载。

## 使用

```
/kp-assistant 你的身份是
/kp-assistant 规则书理智篇112行是什么
/kp-assistant 有玩家打算说服一把锁让它自己打开时，怎么处理
/kp-assistant 弓箭的伤害怎么算
```

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
    │   └── ...（详见索引）
    └── custom/
        ├── general/      # 通用自定义规则
        │   ├── skill-diaomin.md       # 刁民行为处理
        │   ├── skill-kp-assist.md     # KP助理工作流程
        │   └── skill-log-format.md    # log格式规范
        └── module-*/     # 各模组专用数据（按需创建）
```

## 自定义

每个模组有特有数据（怪物、NPC等）时，在 `references/custom/` 下建 `module-<模组名>/` 目录即可，不会影响通用部分。

## 协议

MIT
