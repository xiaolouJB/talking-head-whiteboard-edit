# 口播白板剪辑｜让图解跟着口播走

将口播视频、录音或脚本制作成图解解说视频。先整理实际口播，再依据语义选择白板、流程、对比、关系图、真实材料和总结；默认9:16，可换风格、比例与构图。

入口：[SKILL.md](SKILL.md)。详细外观与表达路线：[风格目录](references/styles.md)。核心包无需绑定ChatCut、花叔引擎或某个模型；实际出片需要当前Agent拥有媒体读取、转写、剪辑、图形渲染与导出能力。

## 使用方式

安装后可直接用中文描述任务：

> 使用口播白板剪辑，把这两段口播合成一条9:16视频。重复内容保留最好的一段，原话不润色；图解跟着口播出现，复杂关系用大白板和右下圆窗，局部讲解切回真人与左上高亮图，结尾做总结。

定制时可补一句：

> 这次改为16:9、黑板粉笔风格，按横屏重新排版，保持原声与内容关系。

或者：

> 这一段讲产品操作，改用真实截图与圈注；其他段落继续清爽白板。

提供脚本而没有录音时，技能先做内容取舍与镜头规划。精确动画同步待音频定时；真人浮窗需要实际真人素材。生成声音、克隆音色、购买素材和上传发布遵循当次任务的授权，不因安装技能而自动获准。

## 安装到Codex

把整个`talking-head-whiteboard-edit`目录放入当前宿主的技能目录。本机采用`~/.codex/skills/talking-head-whiteboard-edit/`；设置了`CODEX_HOME`时按其技能目录使用。

macOS／Linux从通用压缩包解压后的父目录执行：

```sh
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R talking-head-whiteboard-edit "${CODEX_HOME:-$HOME/.codex}/skills/"
```

若同名技能已存在，先比对内容再更新，避免覆盖已有个人修改。安装后在可发现新技能的会话中调用`$talking-head-whiteboard-edit`，或直接描述口播白板剪辑任务。`agents/openai.yaml`提供中文显示名，不属于通用执行的必需文件。

## 安装到Claude Code

本地个人技能放在`~/.claude/skills/talking-head-whiteboard-edit/`；项目共享技能放在项目的`.claude/skills/talking-head-whiteboard-edit/`。

macOS／Linux从解压后的父目录执行：

```sh
mkdir -p "$HOME/.claude/skills"
cp -R talking-head-whiteboard-edit "$HOME/.claude/skills/"
```

在Claude Code中调用`/talking-head-whiteboard-edit`。桌面Cowork与云会话的技能加载方式不同于本地个人目录，按当前官方账号技能导入或项目技能机制使用。

依据：[Claude Code技能文档](https://code.claude.com/docs/en/skills)，核对日期2026-10-11。未在用户的Claude Code客户端做实际安装或视频执行测试。

## WorkBuddy及其他技能宿主

WorkBuddy官方提供本地技能包导入：在技能页面选择添加技能／上传技能，选择压缩包。通用包包含一层技能目录；另提供根目录直接包含`SKILL.md`的压缩包，便于要求该结构的导入器使用。导入器如要求不同层级，应按其提示重新打包，不能靠更改文件扩展名适配。

依据：[WorkBuddy技能说明](https://www.workbuddy.cn/docs/workbuddy/From-Beginner-to-Expert-Guide/Function-Description/Skills-Market)、[开放平台技能结构](https://open.workbuddy.cn/docs/skill)，核对日期2026-10-11。当前交付未在WorkBuddy客户端实测导入。开放平台市场发布还要求额外登记与元数据，本文仅说明个人使用，不自动创建市场发布条目。

通用核心采用[Agent Skills规范](https://agentskills.io/specification)的`name`、`description`与`metadata`字段，不把WorkBuddy市场扩展字段塞进通用入口，避免其他平台的格式校验失败。

## 豆包工作模式与无技能导入入口的平台

此信息未经验证：本次未确认豆包工作模式的官方自定义技能导入格式，也未进行客户端安装测试。可以把`SKILL.md`以及相关参考文档作为任务资料或知识文件提供给能够读取它们的Agent，要求其执行文件中流程。是否支持自动发现、文件系统访问和完整视频渲染，以实际版本和工具能力为准。

其他平台有Agent Skills入口时导入整个文件夹；没有入口时加载文档。文档适配不等同于平台已经拥有视频制作工具。

## 包内内容

- `SKILL.md`：任务触发、默认设置、内容驱动的制作流程。
- `references/styles.md`：9种表达路线、35种艺术风格目录和5种可修改白板外观。
- `references/layout.md`：画幅自适应、真人／图解切换、圆窗、坐标标签、字幕与总结。
- `references/agent-adapters.md`：按宿主真实能力选择制作路线。
- `references/project-contract.md`：可重建的时间映射和图解记录。
- `references/verification.md`：内容、声音、画面与导出核验。
- `agents/openai.yaml`：Codex中文界面元数据，可被其他平台忽略。

格式验证只说明文件结构有效，不能代替在每个客户端实际运行。上游花叔方法来源见风格文档；本包未捆绑其代码、示范角色、字体或素材，不包含私人音色和密钥。
