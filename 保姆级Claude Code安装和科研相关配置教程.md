# 保姆级Claude Code安装和科研相关配置教程
Claude Code 是一个强大的 AI 编程助手，可以帮助你完成帮你编写和修改代码，管理文件和项目，搜索学术文献，执行各种自动化任务等多种任务。

鉴于网上大多数教程都是面向开发者，其安装配置甚至需要科学上网，很是不便。实际上大部分人并不需要编程特化的大模型，国内大模型就够用了。

本教程专为电脑新手设计，详细讲解如何在 Windows 系统上安装和配置 Claude Code。本教程立足国内国内大模型，不需要科学上网。

开始前先点个关注吧！

下载所需文件
------

我已经将所有需要的软件和配置文件打包，你可以从我的网盘一次性下载：

*   **下载链接**：https://pan.baidu.com/s/1xZ7Vo2KQxlSmdWscYHFYRA
    
*   **提取码**：ehjj
    

建议：先将所有文件下载到电脑（建议放在桌面或专门的文件夹），方便后续安装。

 第一步：安装 Git（版本管理工具）
-------------------

 什么是 Git？
---------

Git 就像一个"文件时光机"，它能记录你文件的每一次修改。程序员用它来管理代码版本，Claude Code 也需要用它来理解你的项目结构。

安装方法：
-----

1\. 方法一（推荐）：使用网盘中的 \`Git-2.53.0-64-bit.exe\`

2\. 方法二：从官网下载

*   打开浏览器，访问：https://git-scm.com
    
*   点击 "Download for Windows"
    
*   下载完成后双击安装
    

安装过程：
-----

*   双击安装包
    
*   一直点击 "Next"（下一步）
    
*   遇到选择默认编辑器时，保持默认的 "Vim" 即可
    
*   最后点击 "Install"（安装）
    

![](https://mmbiz.qpic.cn/mmbiz_png/ziavPxIp40Wq63bV6ibicWCYDic7mdsG6FiaVGCTVpS01BFDPV0ePczy3gIc9OKgpkRC1ldYdKYXxOD0lwY0H6yic5KauNkiafCUjWthCQLd3hYSe4/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=0)

验证安装：
-----

*   按`Win + R` 键，输入`cmd`，按回车打开命令提示符
    
*   输入命令并回车：`git  --version`  （注意空格）
    
*   如果看到类似`git version 2.53.0.windows.1` 的版本信息，说明安装成功
    

第二步：安装 Node.js（运行环境）
--------------------

 什么是 Node.js？
-------------

Node.js 让 JavaScript 语言能在你的电脑上运行。Claude Code 是用 JavaScript 写的，所以需要这个环境。

安装方法：
-----

1\. 方法一：使用网盘中的 \`node-v24.13.0-x64.msi\`

2\. 方法二：从官网下载

*   访问：https://nodejs.org
    
*   点击左侧的**LTS 版本**（更稳定）
    

 安装注意事项：
--------

*   安装过程中，找到 "Add to PATH" 选项，**务必勾选**。大多数情况下这个选项是默认勾选的，确认一下就好。
    
*   其他选项都保持默认，一直点 "Next"
    

验证安装：
-----

*   重新打开命令提示符（重要！）
    
*   输入：
    

```nginx
node -v
```

\- 看到版本号如 \`v24.13.0\` 表示成功

3\. 输入：

```nginx
npm -v
```

\- 看到版本号如 \`10.9.2\` 表示成功

\---

第三步：安装 Claude Code 本体
---------------------

 安装命令：
------

*   在桌面空白处，按住`Shift` 键不放
    
*   点击鼠标右键，选择"在此处打开 PowerShell 窗口"
    
*   复制以下命令：
    

```css
npm install -g @anthropic-ai/claude-code
```

4\. 在 PowerShell 窗口中点击右键，命令会自动粘贴

5\. 按回车执行

安装过程：
-----

*   你会看到很多滚动的文字，这是正常的下载过程
    
*   等待 1-3 分钟（取决于网速）
    
*   安装完成后会回到命令提示符
    

验证安装：
-----

输入命令：

```css
claude  --version
```

看到版本号如 \`2.1.x\` 表示安装成功

第四步：配置 Claude Code
------------------

*   找到网盘中的`.claude.json` 文件
    
*   复制这个文件
    
*   打开 C 盘 → 用户 → 你的用户名文件夹
    
*   粘贴到这里（直接放在用户文件夹下，不是某个子文件夹）
    

作用：这个文件让 Claude Code 跳过登录步骤（国内无法访问 Anthropic 官网），并预设了文件管理和文献搜索功能。

第五步：安装 CC-Switch（API 管理工具）
--------------------------

什么是 CC-Switch？
--------------

CC Switch 是目前最方便的CC图形化配置工具，帮你轻松切换不同的 AI 模型（比如 DeepSeek、Kimi 等），还提供托盘快速切换功能。。

1. 安装方法：
--------

方法一（推荐）：使用网盘中的 \`CC-Switch-v3.10.3-Windows.msi\`

方法二：从 GitHub 下载

访问：https://github.com/farion1231/cc-switch/releases/tag/v3.10.1

2. 安装过程：
--------

*   双击`.msi` 文件
    
*   按照提示安装即可
    
*   安装完成后桌面会有快捷方式
    

第六步：配置 AI 模型（以 DeepSeek 为例）
---------------------------

1\. 获取 API Key
--------------

Claude Code 需要一个 "API Key"来连接大模型服务。这里以deepseek为例。

*   打开浏览器，访问：https://platform.deepseek.com
    
*   注册并登录账号
    
*   点击左侧"充值"，先充值 10 元
    
*   点击左侧"API Keys"
    
*   点击"创建 API key"，随便给一个名字，再点击“创建”
    
*   **重要**：生成的`sk-xxx` 开头的密钥只显示一次，立即复制保存！
    

![](https://mmbiz.qpic.cn/sz_mmbiz_png/ziavPxIp40Wq64EZ5bBcbbXbgtiaNnPiagibDEZzNRLYlib029qHQIn9JxJKHh9pSRJjqiazl9hEcLrQiaD5QbX9PiazEtdY5M7ACDYEQzMxpuS9kTQ/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=1)

2\. 在 CC-Switch 中添加 API
-----------------------

*   打开 CC-Switch 软件
    
*   点击最右边的"+"号
    

![](https://mmbiz.qpic.cn/sz_mmbiz_png/ziavPxIp40WrJRseSQeycIobJib3xBGJbTUJD6zMH0B4pdpfCmVkPibHTzI1ag3FY0UvBiaP3AzxDqVySq23GYoiaSicgvSPECrcU1XEwWOFyJccg/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=2)

*   找到 DeepSeek
    
*   粘贴刚才复制的 API Key
    
*   点击"添加"
    

![](https://mmbiz.qpic.cn/sz_mmbiz_png/ziavPxIp40WpF70cZYIicmadG6RktaLVky9XlibxDAEqCpFmCQoCo9xcMic2QU3Tmibrw2YMia8O42JdtXWicNibCHVTtjIlllw0Sk0c0RauFLnr66g/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=3)

现在 Claude Code 就会使用 DeepSeek 作为 AI 模型了！

#### 其他模型可选：

Kimi：https://platform.moonshot.cn（需充值 50 元解锁权限）

智谱 GLM：https://open.bigmodel.cn → API Key

通义千问：https://dashscope.aliyun.com

其他模型类似操作

第七步：测试 Claude Code
------------------

第一次使用：
------

*   打开 PowerShell
    
*   输入：`claude`
    
*   首次使用会有安全检查：
    

![](https://mmbiz.qpic.cn/sz_mmbiz_png/ziavPxIp40WocFGAhURRM53LN0TZ9cYRiaPxXAITCvVCoRYe8jEqAsqq0RxKA38kNZ9na2jUGicZd1jT4VAylEvBVicgVnCuWu9U8xozB2X1kMs/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=4)

*   用键盘上下键选择`1. Yes, I trust this folder`
    
*   按回车确认
    

应该会出现以下界面

![](https://mmbiz.qpic.cn/mmbiz_png/ziavPxIp40WpCDHAKMibImcAO82icsZBSM5f8hPMnp6R8XptxkHZ01s2680b1f2WsxTfficUv1HaJmhUgibWviaQ9Kkd4hOzAWEF50iaFHNMxUJXP0/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=5)

基本测试：
-----

*   输入：你好，然后回车
    
*   如果看到 AI 回复，说明配置成功！
    

![](https://mmbiz.qpic.cn/sz_mmbiz_png/ziavPxIp40WrkaKH8YQksmjsU0n8HLs9Jf5bD4ubTuLC0AaF2PUJicJiaKE78sn3zvXrIFAANibnv4BLwmbPMGEvAoDibiaMmrqdrfvCwIwZJRb1E/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=6)

常用命令：
-----

按下Alt+T可以切换思考模式，用上下键选择，用回车确定。关掉思考（Disabled）会比较快，但是效果可能会差一些。Claude Code会提示你，按回车就行。/help - 查看帮助

/exit - 退出 Claude Code

\-快速按两次 \`Ctrl + C\` 也可以退出

第八步：安装 Python（扩展功能需要）
---------------------

什么是 Python？
-----------

Python 是一种流行的编程语言，很多科学计算和数据处理工具都用它编写。Claude Code 的一些高级功能需要 Python 支持。

安装方法：
-----

1\. 方法一：使用网盘中的 \`python-3.12.9-amd64.exe\`

2\. 方法二：从官网下载

*   访问：https://www.python.org/downloads/release/python-3129/
    
*   下载 Windows installer (64-bit)
    

安装注意事项：
-------

1\. 双击安装包

2\. 重要：在安装界面底部找到 "Add python.exe to PATH"，务必勾选

![](https://mmbiz.qpic.cn/mmbiz_jpg/ziavPxIp40Woib5vMz3fjVQyHyB9LObe4rSzlribic32FGiaLvlbWl6OCaD2jpX0pgNTCcQPBTVQ9r6QpQqxT8hOTFnl4S047ka3gowazOy4M3CA/640?wx_fmt=jpeg&watermark=1#imgIndex=7)

3\. 建议选择 "Install Now"（默认安装）

4\. 等待安装完成

验证安装：
-----

*   打开新的 PowerShell
    
*   输入：
    

```css
python --version
```

3\. 看到版本号如 \`Python 3.12.9\` 表示成功

第九步：安装文献搜索功能
------------

1\. 配置 pip（Python 包管理工具）
------------------------

首先设置清华镜像源，下载更快。复制以下指令，打开 PowerShell，粘贴执行：

```cs
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
```

2\. 安装 Paper Search MCP
-----------------------

```nginx
pip install paper-search-mcp
```

3\. 使用文献搜索
----------

*   打开 Claude Code：
    

```
claude
```

*   查看已安装功能：
    

```bash
/mcp
```

paper-search-mcp上应该有个绿勾，表示已经连上服务器。按ESC键退出mcp界面。

![](https://mmbiz.qpic.cn/sz_mmbiz_png/ziavPxIp40WoricJkgnYVC9sajpcjX2BcJp0eRXDEZYPaibutPzAuhibzBiaO8zVJ74GPox1aBa1EF8dQMQ2paj5LshND1yA2ibYmEwsLh8RcM4GI/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=8)

*   搜索文献：\`搜索今年关于MOF的文献\`
    

*   首次使用需要授权，选择：\`2. Yes, and don't ask again for paper\_search\_mcp\`
    

![](https://mmbiz.qpic.cn/sz_mmbiz_png/ziavPxIp40WrcqkhZcNAGzzQN3T8vWhjZRaGZGDZUoTicic4iakT0ibo4VmrJe9dJH79QicsqKbIxbQibvrBENicCkTPC9XHkppbyvTdnQD7se4O3eQ/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=9)

期间可能会要求授权多次，都选2即可

在我电脑上返回了以下结果

![](https://mmbiz.qpic.cn/mmbiz_png/ziavPxIp40WojicQj1IndicYkCDtkBxJALnrd5cm7ORcc8jyiaOy4pYzl7EoZfZQMPY6eC5g8617YkKlHH5JmLkZWaa9823VelZnahycPZDMDicM/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=10)

 高级搜索：
------

*   指定来源：`请使用 Paper Search MCP 的 search_arxiv 搜索 '人工智能'，返回前5篇`
    
*   指定数量：`搜索10篇关于机器学习的文献`
    

第十步：安装科研写作插件
------------

1\. 安装 Claude Scientific Skills
-------------------------------

这个skill是在github上的，可能有的人无法访问，因此我将这些skill下载下来放在网盘中。

*   下载网盘中的`skills.zip`
    
*   解压到：`C:\用户\你的用户名\.claude\` 文件夹
    

\- 如果 \`.claude\` 文件夹不存在，先创建它

\- 注意文件夹名开头的点号

安装完成后，你的电脑上会有这些重要文件：

```makefile
C:\用户\你的用户名\
├── .claude.json    Claude 配置文件
├── .claude\        Claude 数据文件夹
│   └── skills\     技能插件
└── 其他你的个人文件
```

由于这个SKills有150个之多，我精选了关于科研写作的skill，以及一些生物信息学，化学信息学，数据库，数据统计和作图，以及Claude官方的skill，主要是文档的转换（word，excel，pdf，ppt等），打包成skills.zip供大家使用。如果想要安装更多的skill，可以下载"claude-scientific-skills.zip"，解压缩之后，将里面分类文件夹中对应的skill文件夹拷贝到"C:\\用户\\你的用户名\\.claude\\skills"文件夹即可。同时网盘中还有"claude-scientific-skills简介.xlsx"，这个表格列出了所有的skills的功能，大家可以按需安装。

查看已安装技能：
--------

在 Claude Code 中输入：你有什么技能？

![](https://mmbiz.qpic.cn/sz_mmbiz_png/ziavPxIp40WorLmncu6A0PmVEfgM3GOyzIQs7mED3r1UDYEY3xvXQsnzCoIWyGODUjmjMJZ9uJ3w3vMVhnZ7ciaKqGDMaCiaZazVYp19qHbicSk/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=11)

\#### 2. 安装 Scientific Writer
-----------------------------

打开powershell窗口

```nginx
pip install scientific-writer
```

\#### 3. 初始化科研写作功能
------------------

*   打开 Claude Code
    
*   复制下面的指令，粘贴到claude中，然后回车：
    

```bash
/scientific-writer:init
```

3\. 这会生成一个 \`CLAUDE.md\` 文件，解锁所有科研写作功能

![](https://mmbiz.qpic.cn/mmbiz_png/ziavPxIp40WpdpZIk4AxdqJj5uxNR7N9lVPqYx0COjjKmfWLeYiaaNjpcQP4NIicSMopqyF5HMAgiceoFjsDwHX94Q5c42icksp2DHKgOf7QYq7o/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=12)

第十一步：启动CC的全自动模式

刚开始用 Claude Code 最烦人的是，每执行一个操作都要点确认！直接在启动时加上这个参数：

```css
claude --dangerously-skip-permissions
```

启动后，Claude 会一次性完成全部任务，不再中途询问。你只需提出需求，它会按步骤执行并交付结果。

但是每次输入这么长的指令不免麻烦。所有我将上述指令包装成一个批处理文件："claude-fast.bat"，放在网盘中了。将这个文件复制到"C:\\Program Files\\nodejs\\"下面，以后就可以在终端里直接输入claude-fast.bat，然后回车，进入CC的自动模式

1\. 文件操作
--------

*   创建文件：帮我创建一个 hello.txt，内容写"Hello World"
    
*   读取文件：读取 config.json 文件的内容\`
    
*   修改文件：在 main.py 中添加一个函数
    

2\. 文献研究
--------

*   搜索文献：搜索近三年关于深度学习的综述文章
    
*   下载文献：下载这篇论文的PDF
    
*   文献总结：总结这篇论文的主要贡献
    

3\. 科研写作
--------

*   论文写作：帮我写一篇关于神经网络的小论文
    
*   基金申请：生成一份国家自然科学基金申请书大纲
    
*   文献综述：对2020-2024年AI医疗领域的文献进行综述
    
*   文章润色：帮我润色这段英文摘要
    

 4. 代码开发
--------

*   写代码：用Python写一个计算器程序
    
*   调试代码：帮我找出这段代码的错误
    
*   代码解释：解释这个函数的作用
    

Q1：输入`node -v` 提示"不是内部或外部命令"
----------------------------

原因：Node.js 没有被添加到系统 PATH 中。

解决方法：

*   **简单方法**：卸载 Node.js，重新安装，安装时确保勾选了 "Add to PATH"
    
*   **手动添加**：
    

*   按`Win + I` → 搜索"环境变量" → "编辑系统环境变量"
    
*   点击"环境变量"按钮
    
*   在"系统变量"中找到`Path`，双击打开
    
*   点击"新建"，添加 Node.js 的安装路径，通常是：C:\\Program Files\\nodejs\\
    
*   确定保存，重启终端
    

Q2：`npm install -g` 报权限错误（Permission denied / EPERM）
----------------------------------------------------

原因：没有用管理员权限运行终端。

解决方法：

1\. 关闭当前终端

2\. 点击windows图标，找到Powershell，右键点击Powershell→ "以管理员身份运行"

![](https://mmbiz.qpic.cn/mmbiz_png/ziavPxIp40WqD44TIvuZF7iaBZj1DXux6qicEJwj14Bkj5BWYkqgEgQ1AHFMOpZ8CIJ1Qc2En54QicLlGZG1B041Ze6GrnK9LObktFQIG1epa6s/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=13)

3\. 重新执行安装命令

 Q3：npm 安装速度极慢或超时
-----------------

原因：npm 默认从国外服务器下载，国内访问可能很慢。

解决方法：

```bash
npm config set registry https://registry.npmmirror.com
```

```css
npm install -g @anthropic-ai/claude-code
```

如果想切回官方源：

```bash
npm config set  registry https://registry.npmjs.org
```

Q4：安装完成后输入`claude` 提示"不是内部或外部命令"
--------------------------------

原因：npm 全局安装的路径没有在系统 PATH 中。

解决方法：

1\. 先查看 npm 全局安装路径：

```swift
npm config get prefix
```

2\. 把输出的路径添加到系统 PATH 中（方法同 Q1）

3\. Windows 上通常是：

```makefile
C:\Users\你的用户名\AppData\Roaming\npm
```

Q5：Python 相关功能不能用
-----------------

解决：

*   确认 Python 安装时勾选了 "Add to PATH"
    
*   重启 PowerShell 或电脑
    
*   重新安装 Python
    

Q6：Claude Code 启动慢
------------------

解决：

*   检查网络连接
    
*   确认 API Key 有效
    
*   尝试切换其他模型
    

Q7：文献搜索没反应
----------

解决：

*   确认 paper-search-mcp 安装成功
    
*   检查网络是否能访问学术网站
    
*   重新授权：在 Claude Code 中重新选择授权选项
    

1\. 提高效率
--------

*   使用 Tab 键自动补全命令：命名不用全打出来，打一半的时候按键盘上的Tab（通常在Q键的旁边）科研自动补全命令。
    
*   用上下键查看历史命令
    
*   复杂任务分步进行
    

2\. 学习建议
--------

*   从简单任务开始尝试
    
*   多使用`/help` 查看帮助
    
*   记录常用命令
    

3\. 安全注意
--------

*   不要分享你的 API Key
    
*   重要文件先备份
    
*   谨慎执行删除操作
    

备份配置：
-----

定期备份 \`.claude.json\` 和 \`.claude\` 文件夹，重装系统时可以直接恢复。

你现在已经成功安装并配置了 Claude Code！这是一个功能强大的 AI 助手，可以帮助你：

*   **学习编程** - 随时解答编程问题
    
*   **科研工作** - 文献搜索和论文写作
    
*   **日常办公** - 文件处理和自动化任务
    
*   **创意写作** - 各种文档创作
    

记住：遇到问题不要慌，按照教程检查每一步，或者尝试用 Claude Code 自己解决问题："帮我解决这个错误..."

如果你觉得对你有帮助，请转发让更多人能看到。

“投喂作者小鱼干”