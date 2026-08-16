# Holo 3.1 本地部署教程：用 llama.cpp 接入 OpenClaw 跑 Computer Use Agent
[AI工具](https://knightli.com/categories/ai%E5%B7%A5%E5%85%B7/)

### Holo 3.1 是 H Company 的本地 computer-use Agent 模型。本文整理 Holo 3.1 GGUF 下载、llama.cpp 启动 OpenAI-compatible 服务、OpenClaw 配置 API Base URL 和浏览器自动化 skills 的步骤。

`Holo 3.1` 是 H Company 发布的本地 computer-use Agent 模型系列，定位是视觉语言模型与电脑操作代理。根据官方模型卡，Holo3.1 支持网页、桌面和移动环境，提供 0.8B、4B、9B、35B-A3B 等尺寸，并有适合本地运行的 GGUF 量化版本。

它适合想把 AI Agent 跑在自己电脑上的用户：不走云端 API，不按 token 计费，也更容易把浏览器自动化、桌面操作和本地文件流程控制在自己的机器里。

下面记录一套比较直接的本地部署流程：用 `llama.cpp` 启动 Holo 3.1 的 OpenAI-compatible 服务，再把 OpenClaw 指向本地地址。

准备条件
----

建议准备：

*   Windows、macOS 或 Linux 电脑。
*   一张显存足够的独立显卡，或 Apple Silicon Mac。
*   `llama.cpp` 的 `llama-server`。
*   Holo 3.1 的主模型 GGUF 文件和视觉 `mmproj` 文件。
*   OpenClaw。

模型大小可以按硬件选择：

| 硬件配置 | 推荐模型 |
| --- | --- |
| RTX 4090 / RTX 3090 24GB | 35B-A3B Q4\_K\_M |
| RTX 5070 Ti / RTX 4060 Ti 16GB | 9B |
| Apple Silicon | 9B GGUF |
| 12GB 显存 | 4B |
| 8GB 显存 | 0.8B |

如果只是体验浏览器自动化和简单桌面任务，9B 会更容易跑起来。35B-A3B 更适合 24GB 显存以上机器，但也更吃上下文、显存和加载时间。

1\. 下载 llama.cpp
----------------

可以从 `llama.cpp` releases 下载预编译版本，也可以自己编译。Windows 用户下载后解压，确认目录里有：

然后在 `llama.cpp` 目录下新建：

后续把 Holo 3.1 的主模型和 `mmproj` 文件都放进这个目录。

2\. 下载 Holo 3.1 模型
------------------

Holo 3.1 的官方 Hugging Face 组织为 `Hcompany`。如果使用 `llama.cpp`，需要选择 GGUF 格式。

以 35B-A3B 为例，需要下载：

*   主模型，例如 `Q4_K_M` 量化的 GGUF。
*   对应的视觉投影模型，例如 `mmproj.f16.gguf`。

放入目录后，可以整理成类似结构：

| ```
1 2 3 4 5 
```

 | ```
llama.cpp/  llama-server.exe models/ q4_k_m.gguf mmproj.f16.gguf 
```

 |

文件名可以自定义，但启动脚本里的路径必须对应修改。

3\. 启动 Holo 3.1 本地服务
--------------------

下面是一个 Windows 批处理脚本示例，可以保存为 `start-holo31.bat`，放在 `llama-server.exe` 同级目录。

| ```
 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64 65 66 67 68 69 70 71 72 73 74 75 76 77 78 79 80 81 82 83 84 85 86 87 88 89 90 91 92 93 94 95 96 97 98 99 100 101 102 103 104 105 106 
```

 | ```
@echo off chcp 65001 >nul title Holo 3.1 VLM Launcher   set LLAMA=llama-server.exe   :MENU cls echo ========================================== echo          Holo 3.1 VLM Launcher echo ========================================== echo. echo 1. 8GB GPU  (0.8B) echo 2. 12GB GPU (4B) echo 3. 16GB GPU (9B) echo 4. 24GB GPU (35B-A3B) echo 5. CPU mode (4B) echo 0. Exit echo. set /p CHOICE=Choose:   if "%CHOICE%"=="1" goto GPU8 if "%CHOICE%"=="2" goto GPU12 if "%CHOICE%"=="3" goto GPU16 if "%CHOICE%"=="4" goto GPU24 if "%CHOICE%"=="5" goto CPU if "%CHOICE%"=="0" exit goto MENU   :GPU8 "%LLAMA%" ^ -m models\holo-0.8b.gguf ^ --mmproj models\holo-0.8b-mmproj.gguf ^ -ngl 999 ^ -c 8192 ^ -fa ^ --cache-type-k q4_0 ^ --cache-type-v q4_0 ^ --temp 0.2 ^ --top-p 0.9 ^ --host 127.0.0.1 ^ --port 1234 pause goto MENU   :GPU12 "%LLAMA%" ^ -m models\holo-4b.gguf ^ --mmproj models\holo-4b-mmproj.gguf ^ -ngl 999 ^ -c 16384 ^ -fa ^ --cache-type-k q4_0 ^ --cache-type-v q4_0 ^ --temp 0.2 ^ --top-p 0.9 ^ --host 127.0.0.1 ^ --port 1234 pause goto MENU   :GPU16 "%LLAMA%" ^ -m models\holo-9b.gguf ^ --mmproj models\holo-9b-mmproj.gguf ^ -ngl 999 ^ -c 24576 ^ -fa ^ --cache-type-k q8_0 ^ --cache-type-v q8_0 ^ --temp 0.2 ^ --top-p 0.9 ^ --host 127.0.0.1 ^ --port 1234 pause goto MENU   :GPU24 "%LLAMA%" ^ -m models\q4_k_m.gguf ^ --mmproj models\mmproj.f16.gguf ^ -ngl 999 ^ -c 65536 ^ --flash-attn on ^ --cache-type-k q8_0 ^ --cache-type-v q8_0 ^ --temp 0.2 ^ --top-p 0.9 ^ --repeat-penalty 1.05 ^ --host 127.0.0.1 ^ --port 1234 pause goto MENU   :CPU "%LLAMA%" ^ -m models\holo-4b.gguf ^ --mmproj models\holo-4b-mmproj.gguf ^ -ngl 0 ^ -c 4096 ^ --threads 16 ^ --temp 0.2 ^ --host 127.0.0.1 ^ --port 1234 pause goto MENU 
```

 |

运行脚本后选择对应显存档位。成功后，`llama-server` 会在本地提供 OpenAI-compatible API：

| ```
1 
```

 | ```
http://127.0.0.1:1234/v1 
```

 |

如果启动失败，优先检查三件事：

*   模型文件名是否和脚本一致。
*   `mmproj` 文件是否存在。
*   显存是否足够当前模型和上下文长度。

4\. 安装 OpenClaw
---------------

Windows 以管理员身份打开 PowerShell，执行：

| ```
1 
```

 | ```
powershell -c "irm https://openclaw.ai/install.ps1 | iex" 
```

 |

macOS / Linux 执行：

| ```
1 
```

 | ```
curl -fsSL https://openclaw.ai/install.sh | bash 
```

 |

安装完成后进入 OpenClaw 设置，把模型提供商配置为本地 OpenAI-compatible 服务：

| ```
1 2 
```

 | ```
API Base URL: http://127.0.0.1:1234/v1 API Key: 留空或填写任意占位值 
```

 |

启动模式可以选择浏览器启动。进入 OpenClaw 可视化界面后，应能在底部看到本地模型已加载。

如果界面里有思考模式开关，可以先关闭。Holo 3.1 这类 computer-use Agent 场景更看重动作规划和界面执行，开启额外思考过程可能显著拖慢响应。

5\. 安装浏览器自动化 skills
-------------------

为了让 OpenClaw 更好地操作浏览器，可以安装两个常用 skills：

| ```
1 2 
```

 | ```
openclaw skills install agent-browser-cli openclaw skills install use-my-browser 
```

 |

安装完成后重启 OpenClaw gateway：

也可以在 OpenClaw 对话框里输入：

让它开启新会话并重新加载能力。

6\. 测试一个简单任务
------------

可以先用低风险任务测试：

| ```
1 
```

 | ```
打开浏览器，搜索 Holo 3.1 的官方模型页面，总结它支持的模型尺寸和部署方式。 
```

 |

观察重点不是回答是否漂亮，而是：

*   能否正确打开浏览器。
*   能否识别页面内容。
*   能否连续执行搜索、点击、阅读和总结。
*   是否频繁卡住或重复操作。
*   本地模型响应速度是否能接受。

如果浏览器动作正常，再尝试更复杂的任务，例如整理资料、比较模型页面、生成 Markdown 摘要、分析网页表格等。

使用建议
----

本地 Agent 的优点是成本低、隐私边界清楚、没有云端 token 账单。但它也有现实限制：

*   小模型适合轻量浏览器任务，不适合高难推理。
*   视觉模型对界面识别能力很关键，不能只下载主模型。
*   上下文开太大容易吃显存，建议从保守参数开始。
*   自动化操作有误点风险，不要一开始就让它处理支付、删除、生产系统等高风险任务。
*   本地模型不会自动等于安全，浏览器权限、文件权限和命令执行权限仍然要控制。

如果只是做日常网页资料整理、轻量自动化和本地实验，Holo 3.1 + `llama.cpp` + OpenClaw 是一个值得尝试的组合。它的关键价值不是“免费无限 token”这个口号，而是把 Agent 的运行环境、模型和数据流尽量留在本机。

常见问题
----

### Holo 3.1 是什么？

Holo 3.1 是 H Company 发布的本地 computer-use Agent 模型系列，用于网页、桌面和移动环境中的视觉理解与操作代理任务。

### Holo 3.1 可以本地部署吗？

可以。常见做法是下载 GGUF 量化模型，用 `llama.cpp` 启动 OpenAI-compatible 本地服务，再让 OpenClaw 连接这个 API 地址。

### Holo 3.1 需要什么硬件？

取决于模型尺寸和量化版本。小模型更容易本地实验，35B-A3B 这类版本对显存、内存和推理性能要求更高。

### Holo 3.1 适合什么任务？

适合本地网页资料整理、轻量浏览器自动化、computer-use Agent 实验和隐私敏感的本地工作流。不建议一开始就用于支付、删除或生产系统操作。

参考链接
----

*   Holo 3.1 官方页面：[https://hcompany.ai/holo3.1](https://hcompany.ai/holo3.1)
*   H Company Hugging Face：[https://huggingface.co/Hcompany](https://huggingface.co/Hcompany)
*   Holo 3.1 35B-A3B GGUF：[https://huggingface.co/Hcompany/Holo-3.1-35B-A3B-GGUF](https://huggingface.co/Hcompany/Holo-3.1-35B-A3B-GGUF)
*   llama.cpp：[https://github.com/ggml-org/llama.cpp](https://github.com/ggml-org/llama.cpp)
*   OpenClaw + llama.cpp 设置参考：[https://openclawlaunch.com/guides/openclaw-llamacpp](https://openclawlaunch.com/guides/openclaw-llamacpp)