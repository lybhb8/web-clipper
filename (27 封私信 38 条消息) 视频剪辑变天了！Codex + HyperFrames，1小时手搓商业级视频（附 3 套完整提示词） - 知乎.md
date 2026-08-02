# (27 封私信 / 38 条消息) 视频剪辑变天了！Codex + HyperFrames，1小时手搓商业级视频（附 3 套完整提示词） - 知乎
![](https://pic3.zhimg.com/v2-081ef88055f87e9f06e304b4151cb06c_1440w.jpg)

大家好。我是清风，每天和你一起学 AI 打怪升级。
-------------------------

这是《Codex 实战》系列的第 3 篇。前两篇我们分享了[Codex 的概念、安装和上手](https://zhuanlan.zhihu.com/p/2036461475670270660)；[如何将 codex 转化为算力养 openclaw](https://zhuanlan.zhihu.com/p/2032411822813393651)。

有同学问：**Codex 能不能做视频？**

答案是：不仅能，而且强得离谱。

今天我就用几个真实案例，手把手教你**Codex + [第三方插件](https://zhida.zhihu.com/search?content_id=274699979&content_type=Article&match_order=1&q=%E7%AC%AC%E4%B8%89%E6%96%B9%E6%8F%92%E4%BB%B6&zhida_source=entity)**这套组合拳，不需要剪辑基础，1 小时就能做出以前需要专业团队才能搞定的视频。

以下是今天的内容目录：

*   案例 1：科技[企业宣传片](https://zhida.zhihu.com/search?content_id=274699979&content_type=Article&match_order=1&q=%E4%BC%81%E4%B8%9A%E5%AE%A3%E4%BC%A0%E7%89%87&zhida_source=entity)（15 秒，专业级）
*   案例 2：电影解说短视频（适合抖音影视号）
*   案例 3：回忆杀《那些年玩过的游戏》（可接商单）
*   手把手操作教程+3 套完整提示词
*   进阶技巧（配图+配乐）
*   避坑提醒

⚠️ 重要提示：本文演示的视频效果，均可在 1 小时内由[视频剪辑](https://zhida.zhihu.com/search?content_id=274699979&content_type=Article&match_order=1&q=%E8%A7%86%E9%A2%91%E5%89%AA%E8%BE%91&zhida_source=entity)小白完成。禁止用此方法搬运他人作品。

**一、为什么是 Codex + [HyperFrames](https://zhida.zhihu.com/search?content_id=274699979&content_type=Article&match_order=1&q=HyperFrames&zhida_source=entity)？**
-----------------------------------------------------------------------------------------------------------------------------------------------------------

以前做视频：找素材、学剪辑、配音乐、加动效……一套下来投入极高。

现在有了 AI：**你描述清楚想要的画面，Codex 负责写代码，找素材，做图片，HyperFrames 渲染成片。** 

| 工具 | 作用 | 特点 |
| --- | --- | --- |
| Codex | AI 智能体，理解需求+生成代码 | OpenAI 出品，懂人话 |
| HyperFrames | 视频渲染插件 | 听得懂大白话，上手快 |
| [Remotion](https://zhida.zhihu.com/search?content_id=274699979&content_type=Article&match_order=1&q=Remotion&zhida_source=entity) | 精确帧控制插件 | 适合需要微调的专业用户 |

**两者选择**：新手首选 HyperFrames，而且成片率更高；如果你需要精确到每一帧的调整，用 Remotion。

**二、三个案例，从小白到接单**
-----------------

### **案例 1：科技企业宣传片（提升外部形象）**

**效果**：深蓝黑宇宙质感，HUD UI，科技预告片风格。

> 分析整个网站，https:// [http://nvidia.cn](https://link.zhihu.com/?target=http%3A//nvidia.cn) ，然后制作一个 15 秒的宣传短视频，要求是中文。整体风格、科技、专业、像官方品牌宣传片，融合未来科幻元素与温暖明亮的色彩，展现 [NVIDIA](https://zhida.zhihu.com/search?content_id=274699979&content_type=Article&match_order=1&q=NVIDIA&zhida_source=entity) 在 AI、游戏、自动驾驶、机器人等领域的领导力，并且配上符合场景轻快的背景音乐。

![](chrome-extension://pkpkfhncifckmkkfekjmodjfnjnfcfme/images/default_play_btn.png)

![](https://picx.zhimg.com/v2-344caf374bb3bd8f630dbde12cb865e6.jpg?source=25ab7b06)

00:15

**适合场景**：个人产品启动、轻创业项目、日常小宣传。

### **案例 2：电影解说短视频（适合抖音影视号）**

**效果**：票房排行榜滚动，节奏紧凑。

**提示词**（简化版）：

> 制作一个 15 秒电影票房排行榜短视频，9:16 竖屏。 背景：深色影院风格。 画面：从第 10 名到第 1 名逐条弹出，每部电影配一张封面图。 动效：排名数字放大+弹入效果。 配乐：紧张有节奏感的纯音乐。

**需要准备大量的视频素材。看看效果：** 

![](https://pic1.zhimg.com/v2-69bd238a15a158bcdc1ab0c0676e1f09.jpg?source=25ab7b06)

03:02

**适合场景**：抖音影视号、[自媒体](https://zhida.zhihu.com/search?content_id=274699979&content_type=Article&match_order=1&q=%E8%87%AA%E5%AA%92%E4%BD%93&zhida_source=entity)快速起号。

### **案例 3：回忆杀《那些年玩过的热门游戏》（可接商单）**

这个案例来自网友逸尘

**效果**：游戏画面混剪+情感向配乐，适合闲鱼/抖音接单。

**提示词框架**：

> 制作 30 秒回忆杀视频，主题《那些年玩过的游戏》。 素材：需先收集好一个一个排序（见下方“素材准备”）。 风格：怀旧、温暖、快速混剪。 节奏：前 5 秒慢，中间 20 秒快切，最后 5 秒定格。 配乐：钢琴+[电子鼓](https://zhida.zhihu.com/search?content_id=274699979&content_type=Article&match_order=1&q=%E7%94%B5%E5%AD%90%E9%BC%93&zhida_source=entity)，渐强后收尾。

**适合场景**：闲鱼挂单（毕业季、年会、个人 IP 宣传）。

**三、手把手操作步骤**
-------------

### **第 1 步：安装 Codex App**

下载地址：[https://chatgpt.com/codex](https://link.zhihu.com/?target=https%3A//chatgpt.com/codex)

详细安装教程：见[《Codex 新手指南》](https://zhuanlan.zhihu.com/p/2036461475670270660)（系列第 1 篇）

### **第 2 步：安装 HyperFrames 插件**

1.  进入 Codex App，左侧栏点击“Plugins”
2.  搜索“HyperFrames”，点击“+”号添加

### **第 3 步：制作视频**

输入提示词，在插件中选中 hyperframes

输入提示词

“你访问我的产品网站：http:// 91banana.site，然后使用 /hyperframes 制作一个产品宣传视频”

**codex开始干活啦，给一个完全控制权限。有任何问题，它都可以自己搞定**
---------------------------------------

![](https://pic3.zhimg.com/v2-f894da6a5635ba874d3046990868d0e0_1440w.jpg)

**大概半小时做完**
-----------

![](https://pic2.zhimg.com/v2-b2c92b0e71549ab9752083fffebe262d_1440w.jpg)

消耗了我5小时额度的85%（我开的1.5倍速，最高智能）

![](https://pic2.zhimg.com/v2-474511a2a589cd92eef646e0ca3d0a41_1440w.jpg)

如果不满意，可以让它改，满意就让它导出为mp4（会自动安装[ffmpeg](https://zhida.zhihu.com/search?content_id=274699979&content_type=Article&match_order=1&q=ffmpeg&zhida_source=entity)）

![](https://pic3.zhimg.com/v2-12cb502e593b9c4262cedd96d232e07c_1440w.jpg)

看看效果：

![](https://pic1.zhimg.com/v2-465acb1cb835d24fc29d9d996845ff10.jpg?source=25ab7b06)

00:23

**四、提示词专题**
-----------

写好提示词的核心：**把你脑里的画面翻译成文字**。

必须包含以下要素：

| 要素 | 示例 |
| --- | --- |
| 动画/视频类型 | 功能演示、宣传片、影视解说 |
| 时长和画幅 | 15 秒、9:16 |
| 视频目标 | 让观众理解 NVIDIA 在 AI 领域的领导力 |
| 视觉风格 | Apple 风格、极简科技感、电影感 |
| [关键元素](https://zhida.zhihu.com/search?content_id=274699979&content_type=Article&match_order=1&q=%E5%85%B3%E9%94%AE%E5%85%83%E7%B4%A0&zhida_source=entity) | 必须出现的文字、图片、数据 |
| 动效要求 | 流式打字、淡入淡出、缩放转场 |
| 声音要求 | 配乐风格、有无旁白 |

可以很简单，也可以很复杂：

比如案例一的复杂版如下：

> 请基于当前 Remotion 项目制作 15 秒科技短片《The Future is Rendering》，1920x1080，30fps。背景为深蓝黑宇宙流体质感，需要全屏铺满，并加入轻微 zoom、漂移、暗角和蓝色蒙版。背景要明显可见，但不能抢过前景。整体风格：深蓝黑、蓝紫霓虹、HUD UI、[粒子](https://zhida.zhihu.com/search?content_id=274699979&content_type=Article&match_order=1&q=%E7%B2%92%E5%AD%90&zhida_source=entity)、闪电、科技预告片质感，高级克制。[分镜](https://zhida.zhihu.com/search?content_id=274699979&content_type=Article&match_order=1&q=%E5%88%86%E9%95%9C&zhida_source=entity)：0–3s：中央发光输入框，逐字输入 “Create the future...”，带闪烁光标。3–6s：大量银蓝色 HUD 方框布满全屏，形成[纵深感](https://zhida.zhihu.com/search?content_id=274699979&content_type=Article&match_order=1&q=%E7%BA%B5%E6%B7%B1%E6%84%9F&zhida_source=entity)，依次出现后像被旋涡吸入中心。显示 “Prompt becomes code”。6–10s：四张科技卡片出现：Design、Motion、Systems、Render。随后卡片逐渐放大、轻微震动，最后像玻璃一样整体破碎，包括边框、面板和文字，碎片飞散消失。显示 “Logic becomes motion.”10–13s：一条大的主闪电快速划过，带来横向撕裂感；随后多条闪电布满全屏，最后强闪白。13–15s：最终标题 “The Future is Rendering”，小字 “Built with Codex + Remotion”，定格收尾。要求： 使用 Sequence、AbsoluteFill、useCurrentFrame、interpolate、spring；[组件化](https://zhida.zhihu.com/search?content_id=274699979&content_type=Article&match_order=1&q=%E7%BB%84%E4%BB%B6%E5%8C%96&zhida_source=entity)实现；保留高级科技感；确保可预览和可渲染。

*   **更多提示词案例：** 

产品介绍

> “利用 /hyperframes，创建一个 10 秒的产品介绍，标题淡入，背景为暗色......”

TikTok 风格视频

> “做一个 9 分 16 秒的 TikTok 风格副歌视频......配上弹跳字幕......”

现有文件转化为视频：

上传 PDF / Changelog / CSV / 网站，发出提示理解文件内容，核心内容转视频

以上提示词均在 **HyperFrames 官方文档**中，被列为推荐模板。详见 [https://hyperframes.mintlify.app/guides/prompting](https://link.zhihu.com/?target=https%3A//hyperframes.mintlify.app/guides/prompting)

### **第 4 步：修改与微调**

第一版大概率不会完美。**直接告诉 codex 哪里要改**：

*   ✅ 每次提出修改不要太多
*   ✅ 改完及时预览
*   ✅ codex中截图标注问题位置（操作详见[基础篇](https://link.zhihu.com/?target=https%3A//mp.weixin.qq.com/s%3F__biz%3DMzY4NTI3Njg4MA%3D%3D%26mid%3D2247484676%26idx%3D1%26sn%3D51088e1fe5c4684b500dd19247bfa3b9%26scene%3D21%23wechat_redirect)）  
    确认后，再导出为mp4

**五、进阶技巧（让视频更专业）**
------------------

### **技巧 1：用 Codex 内置 gpt-Image2 生成素材**

示例：

> 帮我生成一个 iPhone 初代的正面图和背面图，参考官方图片，模拟真实模样，图片最好透明背景。

### **技巧 2：用 [Suno](https://zhida.zhihu.com/search?content_id=274699979&content_type=Article&match_order=1&q=Suno&zhida_source=entity) 生成背景音乐**

网站：[http://suno.com](https://link.zhihu.com/?target=http%3A//suno.com)（每天免费额度）

提示词模板：

> 现代电影预告片风格，开头用清脆打击乐+简约钢琴，逐步加入电子贝斯，高潮加入[管弦乐](https://zhida.zhihu.com/search?content_id=274699979&content_type=Article&match_order=1&q=%E7%AE%A1%E5%BC%A6%E4%B9%90&zhida_source=entity)。整体质感高级、干净，类似苹果发布会能量感，纯音乐无人声。

**生成后直接下载，拖进 Codex 项目。** 

旁白配音可以用 [Minimax](https://zhida.zhihu.com/search?content_id=274699979&content_type=Article&match_order=1&q=Minimax&zhida_source=entity) ，海外版支持克隆（[http://www.minimaxi.com](https://link.zhihu.com/?target=http%3A//www.minimaxi.com)）

**六、避坑提醒（网上没人会告诉你）**
--------------------

1.  **不要一次给太多指令**：把需求拆成 3-5 个步骤，让 Codex 一步步做，出错好定位。
2.  **复杂动效用 Remotion**：HyperFrames 听得懂人话，但精确到帧的控制不如 Remotion。
3.  **素材版权**：生成的图片和音乐可商用，但不要直接用他人视频截图。
4.  **额度问题**：Codex Plus 用户每天有一定免费额度，重度使用可考虑 Pro。
5.  **效果问题:** 如果要做出像电影解说，游戏回顾的效果，需要提前准备大量的原始素材。

几天测试下来，我的感受是：**用纯编码形式手搓视频，真的打开了新世界的大门。** 

视频创作的门槛又一次被拉低了。虽然现在还不是尽善尽美，但是是一个发展趋势。

我真心建议所有自媒体人、运营人、市场人都花时间学一学。

**🔒 关注我，下期预告：** 

> 《Codex 实战 (四)：从 0 到 1 手搓一个企业内部[信息管理系统](https://zhida.zhihu.com/search?content_id=274699979&content_type=Article&match_order=1&q=%E4%BF%A1%E6%81%AF%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F&zhida_source=entity)》  
> 我会从一个[项目投资](https://zhida.zhihu.com/search?content_id=274699979&content_type=Article&match_order=1&q=%E9%A1%B9%E7%9B%AE%E6%8A%95%E8%B5%84&zhida_source=entity)管理制度开始，用 Codex 完整搭建一个可用的管理系统。不用写一行代码，全程描述需求即可。