# 首季 AI 漫剧片头编剧 Skill

给**第一季第一集**设计前 15 秒片头分镜，也能审查已有开头是否值得制作。它会先追问主角目标、阻力、失败代价和制作条件，再写逐镜脚本；审稿时按照明确的 100 分标准给出通过或退回结论，不因“画面很酷”就放宽判断。

## 能做什么

- 从故事梗概生成覆盖 0–15 秒的分镜：时间、场景、景别、构图、人物动作、运镜、对白或字幕、声音、叙事作用。
- 给出跨镜稳定的角色与场景视觉锚点，以及供 AI 画面制作参考的提示词草案。
- 审查已有片头：先查一票否决，再逐项评分、指出具体镜头的问题并重写。
- 引用首季参考池时区分“明确第一季”与“未标季数”，不把榜单热度当成成功公式。

## 安装到 Codex

在 macOS 终端执行：

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/soukaibo/ai-comic-opening-writer.git ~/.codex/skills/ai-comic-opening-writer
```

也可以在 GitHub 页面选择 **Code → Download ZIP**，解压后将包含 `SKILL.md` 的文件夹放到 `~/.codex/skills/ai-comic-opening-writer`。打开新的 Codex 对话即可使用；若当前对话未识别新 Skill，重启 Codex 后再试。

以后更新：

```bash
git -C ~/.codex/skills/ai-comic-opening-writer pull --ff-only
```

## 使用方法

在 Codex 对话中点名 `$ai-comic-opening-writer`。例如：

> 使用 $ai-comic-opening-writer。我要做一部横屏玄幻 AI 漫剧的第一季第一集：主角是被逐出宗门的修器师，能听见废剑里的求救声。请先指出开场缺少的关键信息，再写前 15 秒分镜并严格评分。

或把已有片头贴给它审查：

> 使用 $ai-comic-opening-writer。请按评分规程审查这份 15 秒片头。如果没到制作标准，请直接退回并给出修改稿，不要迎合我。

若只给了世界观、没有主角当下的目标或代价，Skill 会先追问。若要求立即出稿，它会明示所用假设，并在评分时照样执行门槛。

## 通过标准

先检查五类一票否决：依赖续季前情、没有可跟随的问题、镜头缺少因果链、15 秒内无法拍清或理解、复制参考作品具体表达。再按具体钩子、首看可理解性、因果递进、人物能动性、15 秒截点、AI 制作一致性和声画文字经济性评 100 分。

**总分至少 80、每个关键维度达到最低分、且无一票否决**，才标为“适合进入制作”。详细分值与审稿反问见 [评分规程](references/rubric.md)。分数用于剧本审稿，不预测播放量。

## 研究依据与文件

2026 年 10 月 20 日的漫剧热播榜前 100 部中，按标题排除 43 部有续季或续作尾号标记的作品；保留 57 部首季候选，其中 **7 部明确第一季、50 部未标季数**。未标季数不等于已核实首发。21 部候选附人工抽帧观察；其余条目主要依靠自动分析。详见 [依据与局限](references/evidence.md)、[候选清单](references/first-season-candidates.csv)和[排除清单](references/excluded-sequels.csv)。

仓库只包含 Skill 文本与筛选清单，**不包含原剧视频、定帧或完整站点数据**。`scripts/build_cohort.py` 是可选的清单重建工具，需要另行提供本地 `enriched_storyboards.json`：

```bash
python3 scripts/build_cohort.py --source /你的本地路径/enriched_storyboards.json
```

抽帧和自动分段不能证实原片的所有对白、声音、动作与运镜；创作时应核对原片。借鉴信息组织方法，不复制参考剧的角色、台词、造型或镜头组合。
