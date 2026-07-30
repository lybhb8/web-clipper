# (26 封私信 / 14 条消息) Claude Code 完全指南：从入门到精通的全面教程 - 知乎
如果你刚开始接触 Claude Code，可能会被各种功能搞得眼花缭乱。

别担心，这份指南将带你系统性地掌握这个强大的工具。我们会从最基础的安装配置讲起，一直到高级的[自动化](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=%E8%87%AA%E5%8A%A8%E5%8C%96&zhida_source=entity)工作流，让你在开发中真正做到事半功倍。

一、环境搭建与基础入门
-----------

### 1.1 安装与身份验证

具体安装过程参考我前面的教程：

[https://mp.weixin.qq.com/s/5N0eNN6PgE0v6QLuhS\_EZw](https://link.zhihu.com/?target=https%3A//mp.weixin.qq.com/s/5N0eNN6PgE0v6QLuhS_EZw)

首次使用时，系统会提示进行身份验证。对于国内用户来讲，通常需要科学上网。因此，可以在C:\\Users\\你的用户名\\.claude\\settings.json里面，添加这一句

```bash
"includeCoAuthoredBy": false 
```

来跳过身份验证过程。

Claude Code 本质上是一个通用的编程 Agent 框架，并不与特定模型绑定。开发者完全可以通过配置[环境变量](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F&zhida_source=entity)，使用国产模型如 [DeepSeek](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=DeepSeek&zhida_source=entity)、GLM、[kimi](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=kimi&zhida_source=entity) 等来驱动 Claude Code，这里推荐使用 [CC Switch](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=CC+Switch&zhida_source=entity) 自由切换。

### 1.2 三种工作模式详解

Claude Code 设计了三种工作模式，每种模式都针对特定的使用场景。理解这些模式的差异，是高效使用 Claude Code 的关键。

默认模式：安全第一

默认模式是最为谨慎的工作方式。在这种模式下，Claude Code 每次创建或修改文件前都会征求用户意见。输入框下方会显示灰色提示“？ For shortcuts”，表明当前处于默认模式。适合重要项目或者对[代码质量](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=%E4%BB%A3%E7%A0%81%E8%B4%A8%E9%87%8F&zhida_source=entity)要求很高的场景。

![](https://picx.zhimg.com/v2-a3e296858fb14902a25cb2e58fda7189_1440w.jpg)

自动模式：效率优先

当输入框下方显示“Accept edits on”时，表示已进入自动模式。在进入这个模式后，Claude Code 会自动处理文件操作，不再反复询问。适合快速原型开发，或者你已经很熟悉它的工作方式。

![](https://pic3.zhimg.com/v2-825caffdb79fe39b214ad9319e3ad0de_1440w.jpg)

[规划模式](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=%E8%A7%84%E5%88%92%E6%A8%A1%E5%BC%8F&zhida_source=entity)：只讨论不写码

规划模式是一个独特的存在。专门用来讨论技术方案、设计架构，不执行具体的代码编写。在做重大重构或复杂功能设计时特别有用。

![](https://pic3.zhimg.com/v2-2a7182be4e10144181537040cf8b6ab0_1440w.jpg)

切换技巧：按 Shift + Tab 可以在三种模式间循环切换，根据当前任务灵活调整。

### 1.3 [终端命令](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=%E7%BB%88%E7%AB%AF%E5%91%BD%E4%BB%A4&zhida_source=entity)无缝集成

不用在多个窗口间切来切去了！Claude Code 可以直接运行终端命令。输入感叹号（!）进入 [Bash 模式](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=Bash+%E6%A8%A1%E5%BC%8F&zhida_source=entity)，然后就能像在普通终端里一样操作。

比如要启动开发服务器，直接输入

要查看文件列表，输入

所有操作都在同一个界面完成，这才是真正的“一体化[开发环境](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83&zhida_source=entity)”。

新文章精选（关注、点赞、收藏，获取第一手信息）
-----------------------

[寻寻觅觅，这才是我想要的Hermes Web UI（强烈推荐）](https://zhuanlan.zhihu.com/p/2028607645859192917)

[一路狂揽5.3万星的Hermes Agent 安装指南来了](https://zhuanlan.zhihu.com/p/2026310080262357049)

[打工人必备 AI 新三件套：NotebookLM、Claude Code、Obsidian](https://zhuanlan.zhihu.com/p/2024133568557761035)

[我用两周时间踩完openclaw所有坑，总结出这份完整调教指南](https://zhuanlan.zhihu.com/p/2016823158380995920)

[我用 OpenClaw 搞了家16人的公司：全员AI，24小时无休！](https://zhuanlan.zhihu.com/p/2018259939664109626)

[把 OpenClaw 装在本地电脑 24 小时工作，6000 字零基础上手教程](https://zhuanlan.zhihu.com/p/2019706301387666666)

[OpenClaw下载量 Top 20 的神仙级技能包分享](https://zhuanlan.zhihu.com/p/2019428885486388929)

[OpenClaw 十大痛点破解：10 个 Skills 直接对症下药](https://zhuanlan.zhihu.com/p/2022606975700145296)

[Claude Code 深度用法指南：那些让效率翻倍的隐藏技巧](https://zhuanlan.zhihu.com/p/2024783081865846798)

二、核心功能与日常使用
-----------

### 2.1 初始设置与个性化配置

中文界面设置

Claude Code的/config指令 提供了多项配置选项。输入 /config 打开设置面板，找到 language 选项，改成中文。这样 Claude Code 就会用中文和你对话，沟通更顺畅。

![](https://pic4.zhimg.com/v2-d70c1b8f2d05fad293f26c441035e54b_1440w.jpg)

输出风格选择（重要但容易被忽略的设置）

```text
命令：/config → Output Styles
```

这个设置特别重要但容易被忽略。在 /config → Output Styles 里，有两个推荐选择：

详细解释模式（Explanatory）：每次修改都会说明为什么这么改，适合学习和理解

![](https://pic1.zhimg.com/v2-98cf560a0be9dd6dd1cced5283b796aa_1440w.jpg)

学习引导模式（Learning）：给你 TODO 列表，让你自己动手实践，适合想深入学习的人

自动更新通道：选择稳定的更新策略

在 /config → Auto-update channel 里选 stable 通道。虽然功能更新慢一点，但更稳定，不容易遇到奇怪的 Bug。

模型切换：快慢结合

用 /model 命令可以在不同模型间切换：

[Sonnet](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=Sonnet&zhida_source=entity)：速度快，适合日常写代码、调试、做小工具

[Opus](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=Opus&zhida_source=entity)：更聪明，适合[架构设计](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=%E6%9E%B6%E6%9E%84%E8%AE%BE%E8%AE%A1&zhida_source=entity)、复杂问题分析

建议的用法：平时用 Sonnet 快速开发，遇到棘手的设计问题时切到 Opus 深度思考。

自定义 Output Style：创建专属交互风格

你可以让 Claude Code 变成你专属的“老师”。比如输入

```bash
/output-style:new I want a style that teaches Next.js best practices.
```

然后按提示设置，以后就能随时切换到“Next.js [最佳实践](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=%E6%9C%80%E4%BD%B3%E5%AE%9E%E8%B7%B5&zhida_source=entity)教练”模式。

其他可创建的自定义风格包括： - [技术写作](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=%E6%8A%80%E6%9C%AF%E5%86%99%E4%BD%9C&zhida_source=entity)助理风格 - 代码评审导师风格 - 特定框架或语言的专属风格

### 2.2 核心命令，提升日常效率

/clear —— 清空对话历史

完成一个功能开发后，输入 /clear 清空所有历史对话。这样既节省 Token，也让新对话更专注。

/compact —— 智能压缩对话

与 clear 不同，compact 不是清空上下文，而是对其进行总结和压缩。

长时间聊天后，Claude Code 可能会“记忆混乱”。输入 /compact 可以智能压缩历史对话，保留核心信息，让它重新“清醒”起来。

小技巧：输入 /compact 后按 Tab，可以加参数，比如 /compact 保留用户管理功能相关内容。

/context —— 可视化查看 Token 使用情况

想知道 Claude Code 用了多少 Token？输入 /context 可以看到[可视化](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=2&q=%E5%8F%AF%E8%A7%86%E5%8C%96&zhida_source=entity)的使用情况图表，一目了然。

/copy —— 快速复制结果

需要把 Claude Code 的回答保存下来？输入 /copy 就能把最后一次回复以 Markdown 格式复制到剪贴板。

/export —— 导出完整对话

想备份整个对话记录？输入 /export 可以选择导出到文件或剪贴板，方便日后查阅。

### 2.3 [项目管理](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=%E9%A1%B9%E7%9B%AE%E7%AE%A1%E7%90%86&zhida_source=entity)，让工具记住你的项目

让 Claude Code 为你的项目生成一个“说明书”。对它说：“生成一个 CLAUDE.md，总结本项目的[技术栈](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=%E6%8A%80%E6%9C%AF%E6%A0%88&zhida_source=entity)、目录结构和约定。” 这个文件会放在[项目根目录](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=%E9%A1%B9%E7%9B%AE%E6%A0%B9%E7%9B%AE%E5%BD%95&zhida_source=entity)，以后 Claude Code 就会按照里面的规则来工作。

当它理解错了你的项目规则时，及时补充：“请把这条规则写进CLAUDE.md。” 这个文件会随着项目一起成长。

/init —— 初始化记忆文件

接手新项目时，在项目目录输入 /init。Claude Code 会自动分析项目结构，给你一份清晰的“项目导览”。想用中文的话，输入 /init 使用中文。

典型使用场景：

*   刚 clone 的[开源项目](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=%E5%BC%80%E6%BA%90%E9%A1%B9%E7%9B%AE&zhida_source=entity)
*   接手他人的现有项目
*   重新查看自己很久未接触的代码

输入 /init 后，Claude Code 会执行以下操作：

*   扫描项目结构
*   概括项目功能
*   说明如何运行和主要入口位置
*   标记关键模块和配置

将 /init 作为项目导览的起点，有助于快速理解陌生[代码库](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=%E4%BB%A3%E7%A0%81%E5%BA%93&zhida_source=entity)。

/memory —— 编辑记忆文件

输入 /memory 可以直接编辑记忆文件。这里可以设置[代码风格](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=%E4%BB%A3%E7%A0%81%E9%A3%8E%E6%A0%BC&zhida_source=entity)、开发规范等，让 Claude Code 更符合你的工作习惯。通过此功能可以配置编程风格、代码规范等，使 Claude Code 更符合个人工作习惯。

### 2.4 会话管理，高效组织工作

/rename —— 给当前对话重命名

长时间开发中会有多个对话。输入 /rename 加 Tab，然后起个有意义的名字，比如 用户认证功能开发，以后找起来更方便。

/resume —— 继续之前的对话

想接着上次没聊完的话题？输入 /resume 会列出所有历史对话，选一个就能无缝衔接。

/status —— 实时监控状态

输入 /status 可以看到当前会话的详细信息：用的什么模型、还剩多少 Token、大致成本多少。特别是有配额限制时，定期看看这个很有用。

主要看三件事：

*   剩余 token / 使用额度
*   当前使用的模型
*   最近会话的大致成本

在有配额限制或团队共享额度的场景中，定期查看 /status 可以避免额度突然耗尽的情况。

/statusline —— 定制状态栏

输入 /statusline 可以定制输入框下方的状态栏。比如设置显示模型和剩余上下文比例，随时掌握资源情况。

/usage —— 查看使用量

如果你是 Pro 用户，输入 /usage 可以看到详细的使用统计，方便管理配额。

三、高级功能，解锁更多可能性
--------------

### 3.1 复安全与权限，平衡效率与风险

终端命令授权

即使在自动模式下，运行终端命令也需要你授权。Claude Code 提供了三个选项：单次授权、目录级授权、拒绝。

这是因为终端命令可能带来风险，比如删除文件、修改系统配置。这种设计在便利性和安全性之间找到了平衡。

完全权限模式（慎用）

追求极致效率的话，可以在启动时加上 –dangerously-skip-permissions 参数。这样 Claude Code 就获得了完全终端权限，所有操作不再询问。

注意名字里的 “dangerously”——确实有风险。虽然正常情况下 Claude Code 不会做破坏性操作，但它理论上拥有了和你一样的系统权限。

后台任务管理

启动开发服务器（npm run dev）后，服务会阻塞 Claude Code 的交互。按 Ctrl + B 可以把服务放到后台运行。

输入 /tasks 查看所有后台任务，按 K 键终止选中的任务。这样就能同时运行多个长期进程，不影响正常使用。

[版本回滚](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=%E7%89%88%E6%9C%AC%E5%9B%9E%E6%BB%9A&zhida_source=entity)及其局限性

按 –rewind 或双击 ESC 可以进入回滚界面，选择回滚到某个历史状态。

但要注意：Claude Code 只能回滚它自己写入的文件。通过终端命令创建的文件（比如 [mkdir](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=mkdir&zhida_source=entity) 建的目录、npm install 装的依赖）无法回滚。所以 [Git](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=Git&zhida_source=entity) 还是必不可少的。

### 3.2 分层配置，智能又省钱的方案

Claude Code 支持通过 claude.md 文件配置规则，而且可以分层管理：

1.父目录规则：在项目父目录放一个 claude.md，定义通用规则，子项目都能共用

2.语言专属规则：在 js、python 等目录放专属的 claude.md

3.避免全部放个人目录：如果把所有规则都放在用户目录，每次对话都会传输大量规则，浪费 Token 还多花钱

这种[分层设计](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=%E5%88%86%E5%B1%82%E8%AE%BE%E8%AE%A1&zhida_source=entity)既保证了规则共享，又控制了成本。

### 33 Hook：自动化你的重复工作

Hook 让 Claude Code 在特定时机自动执行任务。输入 /hooks 进入配置界面。

典型应用：代码自动格式化。配置一个 post-tool-use Hook，在 Claude Code 编辑文件后自动运行 Prettier。这样每次修改完代码，都会自动格式化，保持风格统一。

Hook 可以保存在三个级别：只在本机生效、项目团队成员共享、个人专属配置。

### 3.4 Agent Skill：可复用的任务模板

Agent Skill 就像是给 Claude Code 看的“任务说明书”。在 ~/.claude/skills/ 目录下创建 skill.md 文件，定义任务的标准流程。

比如创建一个“每日总结”Skill，定义总结应该包含哪些部分、用什么格式。以后让 Claude Code 做每日总结时，它就会按照这个模板来执行。

使用 Skill 有两种方式：Claude Code 自动匹配，或者你用 /skill-name 显式调用。

### 3.5 Sub-Agent：独立的重型任务处理

有些任务太复杂，不适合在主对话中进行。比如分析几万行代码，生成详细报告。如果这些中间过程都进入主对话，很快就会把上下文窗口塞满。

这时候可以用 Sub-Agent。输入 /agent 创建一个独立的 Agent，它在自己的空间里完成任务，只把最终结果返回给主对话。主对话保持清爽高效。

### 3.6 Plugin：一键部署完整解决方案

Plugin 是把多个 Skill、Agent、Hook 打包在一起的完整解决方案。比如官方提供的“Frontend Design”插件，包含了 UI 设计的最佳实践。

输入 /plugin 进入[插件管理器](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=%E6%8F%92%E4%BB%B6%E7%AE%A1%E7%90%86%E5%99%A8&zhida_source=entity)，可以浏览、安装、管理插件。安装后，Claude Code 在设计界面时就会自动应用这些最佳实践。

四、高效工作流与技巧
----------

### 4.1 规划模式：先想清楚再动手

做大型功能开发或重构时，需要先讨论清楚再写代码。虽然可以手动备注“先讨论需求”，但多轮讨论下来很繁琐。

解决方案：按 Shift + Tab 两次进入规划模式。在这个模式下，Claude Code 只讨论不写码，专注把方案打磨完善。

技巧：规划模式下要用 Shift + Enter 换行，直接按回车会提交请求。需要输入大量文字时，按 Ctrl + G 打开 VS Code 编辑器，在熟悉的环境里编辑更舒服。

### 4.2 高效换行技巧

在 Claude Code 里输入时，换行是常见操作。有两个方法：

通用方法：Ctrl + J 所有终端都支持，想换多少行都行。刚开始可能不习惯，用几次就好了。

部分终端：Shift + Enter 在 Cursor、iTerm 2 终端里可以用。先运行 terminal setup 命令启用。

注意：[Warp 终端](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=Warp+%E7%BB%88%E7%AB%AF&zhida_source=entity)不支持这个方法，所以还是推荐用 Ctrl + J，兼容所有情况。

### 4.3 实时插话：不用等它做完

传统工具要么等任务结束，要么强制终止。Claude Code 支持实时插话：任务执行中，你可以随时插入新指令。

比如让它开发一个游戏，中途你觉得方案不好，直接说“算了，用另一个方案”，它会自动理解并调整。这才是真正的[智能协作](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=%E6%99%BA%E8%83%BD%E5%8D%8F%E4%BD%9C&zhida_source=entity)。

### 4.4 快速取消：一键中断

如果明确任务不需要继续，按 Escape 键立即终止，界面会显示“Interrupted by User”。

### 4.5 不同深度思考

思考模式切换：根据任务需求选择思考或者不思考

命令：Alt+T

关掉思考（Disabled）：响应速度快，适合日常编码、调试、小型工具开发。

思考模式：推理能力更强，适合架构设计、复杂重构、[性能优化](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=%E6%80%A7%E8%83%BD%E4%BC%98%E5%8C%96&zhida_source=entity)等需要深度思考的场景。

想让 Claude Code 做更深度的分析？在提示词末尾加上特定关键字：

think：基础思考

think hard：深度思考

think harder：更深度思考

ultra think：极致深度思考

比如：“这个文件很复杂，分析一下并提出三种重构方案，[ultra think](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=2&q=ultra+think&zhida_source=entity)”。它会从多个维度深入分析每个方案。

### 4.6 上下文管理：保持最佳状态

长时间开发后，Claude Code 的上下文会积累大量信息，影响性能和 Token 消耗。

定期用 /compact 压缩上下文，智能保留核心信息。完全不相关的任务切换时，用 /clear 清空所有上下文，从头开始。

五、最佳实践，构建高效工作流
--------------

### .1 根据阶段调整模式

•[快速原型](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=2&q=%E5%BF%AB%E9%80%9F%E5%8E%9F%E5%9E%8B&zhida_source=entity)：用自动模式，让 Claude Code 自由发挥

•生产开发：切回默认模式，精细控制每个变更

•架构设计：先规划模式讨论，确定方案再执行

### 5.2 权限管理：安全第一

•个人学习项目：可以放宽权限提高效率

•团队协作项目：保持严格权限控制

•生产环境：绝对不要用 –dangerously-skip-permissions

### 5.3 定期清理上下文

定期用 /compact 压缩，不相关的任务用 /clear 清空。就像电脑内存管理一样，适时的清理让系统运行更流畅。

### 5.4 构建分层配置体系

•基础规范写在全局配置

•技术栈规则写在对应目录配置

•项目特定规则写在项目配置

这样既保证了规则共享，又避免了配置臃肿。

断演进，变得更加精准和高效。

六、故障排除与优化
---------

/doctor：问题诊断工具

Claude Code 行为异常时（比如配置不生效、权限问题），先别急着重装。输入 /doctor 让它自动检查配置和环境。

很多常见问题（模型没选对、权限不足、配置冲突）都能通过这个命令直接定位。

七、给新手的起步建议
----------

如果你刚接触 Claude Code，做好这两件事就能显著降低学习成本：

1.先把 Output Style 设为详细解释模式，让 Claude Code 边做边解释

2.为每个项目生成 CLAUDE.md，并在开发中持续更新

当工具越来越“懂”你和你的项目时，学习曲线自然就平缓了。

八、不仅仅是[代码生成](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=%E4%BB%A3%E7%A0%81%E7%94%9F%E6%88%90&zhida_source=entity)工具
-----------------------------------------------------------------------------------------------------------------------------------------------------------------

Claude Code 代表的是一种新的开发范式：将 AI 能力深度融入开发工作流。它的价值不仅在于生成代码的速度，更在于提供了一个完整的、可扩展的智能开发环境。

真正的秘诀在于理解其[设计理念](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=1&q=%E8%AE%BE%E8%AE%A1%E7%90%86%E5%BF%B5&zhida_source=entity)：灵活的模式切换、精细的[权限控制](https://zhida.zhihu.com/search?content_id=273780111&content_type=Article&match_order=2&q=%E6%9D%83%E9%99%90%E6%8E%A7%E5%88%B6&zhida_source=entity)、开放的扩展机制、智能的上下文管理。通过这些特性，Claude Code 成为了一个既强大又可控的合作伙伴。

记住：工具的价值在于如何使用。Claude Code 给了你强大的能力，如何发挥这些能力，取决于你的智慧和实践。保持探索精神，不断尝试新的工作方式，找到最适合你的使用模式，这才是提升开发效率的真正关键。[网页链接](https://link.zhihu.com/?target=https%3A//mp.weixin.qq.com/s/5N0eNN6PgE0v6QLuhS%255C_EZw)记住：工具的价值在于如何使用。Claude Code 给了你强大的能力，如何发挥这些能力，取决于你的智慧和实践。保持探索精神，不断尝试新的工作方式，找到最适合你的使用模式，这才是提升开发效率的真正关键。