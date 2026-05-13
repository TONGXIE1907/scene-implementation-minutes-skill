# Meeting Minutes Skill

AI 驱动的会议纪要生成 Skill，专为 **平台培训 + 需求收集** 场景优化。skill里的会议概要的培训方或者会议主题可以进行一个自定义

## 适用场景

- 甲方企业平台培训会议
- 业务需求采集调研会议
- 任何带时间戳的会议录音转写文本

## 输入格式

支持**只有时间戳、无说话人标注**的会议转写文本。AI 会根据语义自动判断发言方和部门归属。

## 输出结构

生成包含以下 9 个章节的完整 Markdown 会议纪要：

1. **会议概览** — 时间、地点、参会方、主题
2. **培训内容记录** — AI 概念、平台架构、场景演示、答疑讨论
3. **需求采集（按部门）** — 每个需求的 6 维度深度解剖
   - 痛点描述
   - 当前人工操作步骤
   - 涉及的数据源
   - 判断/决策逻辑
   - 客户预期结果
   - 需求流转流程图（Mermaid）
4. **数据源与系统对接汇总** — 跨部门数据源总表
5. **跨部门协同关系图** — Mermaid 流程图
6. **思维导图** — Mermaid mindmap 全局总览
7. **会议整体流程图**
8. **待办事项** — 分客户方/培训方，含紧急程度
9. **下次培训/沟通计划**

## 安装

### Claude Code

```bash
mkdir -p ~/.claude/skills/meeting-minutes
cp SKILL.md ~/.claude/skills/meeting-minutes/
```

安装后 Claude Code 会自动发现，无需额外配置。

### 其他 AI 平台

如果平台不支持 skill 机制，直接将 `SKILL.md` 的内容复制到对话开头作为 system prompt，效果完全相同。

## 使用

在 Claude Code 中，直接粘贴培训会议录音转写文本，Skill 会自动触发。也可以使用斜杠命令：

```
/meeting-minutes
```

然后粘贴文本即可。

## 与 Web 应用的配合

此 Skill 提取自 [Meeting Minutes Generator](https://github.com/TONGXIE1907/meeting-minutes) 项目。如果你需要：
- **Web 界面**（上传文件、进度条、历史记录）→ 使用完整项目
- **语音转文字**（M4A/MP3 → 文本）→ 使用完整项目的 whisper_worker
- **纯文本直接生成纪要**（最快路径）→ 使用此 Skill

## License

MIT
