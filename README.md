# Claude Skills 合集

个人自制的 [Claude Code Skills](https://docs.claude.com/en/docs/claude-code/skills) 仓库。每个 skill 是一套打包好的工作流，装上后 Claude 会在对应任务场景自动触发。

## 安装

把需要的 skill 复制到你的 Claude 技能目录（二选一）：

```bash
# 全局安装（所有项目可用）
cp -R skills/<技能名> ~/.claude/skills/

# 仅当前项目
cp -R skills/<技能名> <你的项目>/.claude/skills/
```

重启 Claude Code 会话后生效。新会话里可用 `/skills` 或让 Claude 列出技能确认加载。

## Skills 列表

| 技能 | 用途 | 适用场景 |
|---|---|---|
| [one-minute-story-bible](skills/one-minute-story-bible/) | 一分钟 AI 萌宠短视频的完整制作圣经：从立项到 Seedance 2.0 提示词 | 小猫旅居 vlog（芋仔）的故事大纲 / 剧本 / 分镜 / 视频提示词 |

---

## one-minute-story-bible 详解

**一句话**：用逐阶段确认的流程，把"小猫旅居"的一分钟故事从立项做到可交付的分镜与 Seedance 2.0 视频提示词。

**核心原则**：一条消息只推进一个阶段；没有用户明确确认，绝不进入下一阶段。

### 八阶段流程

| 阶段 | 名称 | 产出 |
|---|---|---|
| 0 | 立项卡 | 故事类型、目的地、时长、情绪核心、观众带走的一句话 |
| 1 | 故事脊柱 | logline、欲望、阻碍、转折、结尾画面 |
| 2 | 节拍大纲 | 按故事类型的节拍表，含时长与情绪变化 |
| 3 | 完整剧本 | 场景、时长、画面、台词、声音、连续性 |
| 4 | 分场剧情节拍 | 每场戏拆 2–4 个节拍，标明变化 |
| 5 | 分镜表 | ≤9 镜，含景别、运镜、画面、台词、声音 |
| 6 | Seedance 2.0 提示词 | 每镜一条结构化提示词 + 参考图映射 + 负面约束 |
| 7 | 交付质检 | 按清单逐项检查，输出交付包 |

每阶段结束固定以「【阶段 N · 等待确认】」收尾，用户确认后才推进。上一集的确认不覆盖下一集。

### 硬规则速览

- **时长**：标准集 50–65 秒；低成本测试可用 30 秒首版（6–7 镜，图生视频 ≤2）
- **镜头**：≤9 镜，每镜 2–8 秒，一镜一个主要动作、一个主要运镜
- **人类**：不出正脸和身体，最多手部
- **角色**：芋仔是四足布偶猫，不穿衣服（锚点见 `references/story-bible.md`）
- **风格**：每条提示词必须带视觉风格锚点（A 底色 + B/C 构图变体），9:16 竖屏，画面无文字
- **片尾**：固定电量卡「辞职第 N 天 / 电量 XX% / 下一站:XX」，只写结果不解释
- **台词**：第一人称短句，不煽情不讲道理
- **合规**：发布勾选 AIGC 标识；不编救助/领养情节
- **成本**：先生成 480p 草稿，单镜重试 ≤3 次

### 文件结构

```
one-minute-story-bible/
├─ SKILL.md                       # 主技能：阶段地图、确认协议、硬规则
└─ references/
   ├─ story-bible.md              # 芋仔世界观、性格、声音、硬约束
   ├─ story-types.md              # 五种故事类型与节拍模板
   ├─ visual-style.md             # 参考图视觉风格与三层提示词锚点
   ├─ script-standard.md          # 剧本格式标准
   ├─ storyboard-standard.md      # 分镜表格式与镜头规则
   ├─ seedance-prompt-guide.md    # Seedance 2.0 提示词规范
   ├─ templates.md                # 各阶段输出模板
   └─ delivery-checklist.md       # 交付质检清单
```

## 更新日志

- **2026-11-16**：仓库创建，收录 `one-minute-story-bible` v1

## License

待定（如需 MIT 等许可，联系仓库作者）。
