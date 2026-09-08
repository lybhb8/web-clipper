# GitHub 这个隐藏神技太绝了！免费用上 64 核 CPU + 16G 内存云主机！什么宽带能跑到 4.6Gbps？Tailscale + RDP 远程桌面保姆级部署教程。 | 数码解码的博客
[数码攻略](https://smjmbk.xyz/categories/%E6%95%B0%E7%A0%81%E6%94%BB%E7%95%A5/)[GitHub](https://smjmbk.xyz/categories/%E6%95%B0%E7%A0%81%E6%94%BB%E7%95%A5/GitHub/)[GitHub Actions](https://smjmbk.xyz/tags/GitHub-Actions/)[Tailscale](https://smjmbk.xyz/tags/Tailscale/)[RDP](https://smjmbk.xyz/tags/RDP/)[Windows Server](https://smjmbk.xyz/tags/Windows-Server/)[云电脑](https://smjmbk.xyz/tags/%E4%BA%91%E7%94%B5%E8%84%91/)[免费VPS](https://smjmbk.xyz/tags/%E5%85%8D%E8%B4%B9VPS/)[内网穿透](https://smjmbk.xyz/tags/%E5%86%85%E7%BD%91%E7%A9%BF%E9%80%8F/)[挂机保活](https://smjmbk.xyz/tags/%E6%8C%82%E6%9C%BA%E4%BF%9D%E6%B4%BB/)2026-09-072026-09-04

[![](https://cdn.jsdelivr.net/gh/hallteacher/2026-8tuchuang/smjm/20260904170013819.png)
](https://cdn.jsdelivr.net/gh/hallteacher/2026-8tuchuang/smjm/20260904170013819.png)

[](#Tailscale官方网站：【点击前往】 "Tailscale官方网站：【点击前往】")Tailscale官方网站：[【点击前往】](https://tailscale.com/)
----------------------------------------------------------------------------------------------

[](#github官方网站：【点击前往】 "github官方网站：【点击前往】")github官方网站：[【点击前往】](https://github.com/)
----------------------------------------------------------------------------------

[](#先说清楚这个方案是什么，以及需要注意什么 "先说清楚这个方案是什么，以及需要注意什么")先说清楚这个方案是什么，以及需要注意什么
--------------------------------------------------------------------

这次实测的方案，核心思路是利用 GitHub Actions（GitHub 提供的自动化工作流工具，本意是给开发者做代码构建、测试、部署用的）来触发创建一台运行在微软 Azure 云上的 Windows 虚拟机，再通过 Tailscale（一款基于 WireGuard 协议的虚拟组网工具）实现不需要公网 IP 就能远程连接。

**在开始教程之前，有一点需要说清楚**：GitHub Actions 官方设计的用途是持续集成和持续部署（CI/CD），也就是自动化构建、测试代码这类任务，并不是为了让用户拿它长期跑一台远程桌面虚拟机。这类”借道” GitHub Actions 搭建持久化云主机的做法，虽然在技术圈子里流传比较广，但严格来说属于 GitHub 使用条款里不太提倡的用法，存在账号被限制或者工作流被终止的风险。这次实测是为了记录技术上是如何实现的，如果你打算长期依赖这套方案，建议提前评估好这个风险，不要把重要数据或者关键业务放在这类非官方支持的免费方案上。

了解这个前提之后，下面是完整的搭建流程。

[![](https://cdn.jsdelivr.net/gh/hallteacher/2026-8tuchuang/smjm/20260904170104803.png)
](https://cdn.jsdelivr.net/gh/hallteacher/2026-8tuchuang/smjm/20260904170104803.png)

[](#Tailscale-是什么 "Tailscale 是什么")Tailscale 是什么
-----------------------------------------------

Tailscale 是一款虚拟组网与零信任访问平台，核心作用是把分散在不同网络环境下的设备（比如云服务器、个人电脑）连接进同一个虚拟网络，让这些设备之间可以像在同一个局域网内一样直接互通，不需要公网 IP、不需要手动配置端口转发，这也是这套方案能绕开”没有公网IP就无法远程连接”这个限制的关键工具。

[](#第一步：注册-Tailscale-账号 "第一步：注册 Tailscale 账号")第一步：注册 Tailscale 账号
-----------------------------------------------------------------

来到 Tailscale 官网，点右上角”免费开始”，登录方式支持微软账号等多种方式，选择微软账号登录，点”下一步”，”接受”授权。

接下来会有几个简单的问卷设置：使用场景选择”VPN替代”，身份选择”学生”（或者按自己实际情况选择），最后问”在哪里知道这个网站”，随便选一个提交即可。

进入主页面后，点击”添加第一个设备”，选择下载 Windows 版 Tailscale 客户端，下载完成后双击安装，勾选协议同意，点击”Install”完成安装。安装完成后，Tailscale 会自动为这台设备分配一个专属的虚拟局域网 IP 地址。

[](#第二步：创建-GitHub-仓库并配置工作流文件 "第二步：创建 GitHub 仓库并配置工作流文件")第二步：创建 GitHub 仓库并配置工作流文件
--------------------------------------------------------------------------------

打开 GitHub，点击头像进入个人主页，点击加号创建一个新仓库，仓库名称随便起，README 文件这里可以直接关闭不勾选，点击创建仓库。

仓库创建好之后，点击”添加文件”→”创建新文件”，文件名需要按照工作流配置文件的标准路径命名（这类配置通常放在 `.github/workflows/` 目录下），提交更改保存。

```bash
windows-rdp.yml
```

```bash
name: Windows Cloud RDP

on:
  workflow_dispatch:

jobs:
  build:
    runs-on: windows-latest
    timeout-minutes: 360

    steps:
      - name: 1. Enable Remote Desktop & Firewall
        run: |
          Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server' -name "fDenyTSConnections" -Value 0
          Enable-NetFirewallRule -DisplayGroup "Remote Desktop"
          Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp' -name "UserAuthentication" -Value 0

      - name: 2. Create Admin Account
        run: |
          $Password = ConvertTo-SecureString "P@ssw0rd1qazXSW@#" -AsPlainText -Force
          New-LocalUser -Name "NvdAdmin" -Password $Password -PasswordNeverExpires -ErrorAction SilentlyContinue
          Add-LocalGroupMember -Group "Administrators" -Member "NvdAdmin" -ErrorAction SilentlyContinue
          net user runneradmin P@ssw0rd1qazXSW@#

      - name: 3. Install & Connect Tailscale VPN
        env:
          TAILSCALE_AUTHKEY: ${{ secrets.TAILSCALE_AUTHKEY }}
        run: |
          
          Invoke-WebRequest "https://pkgs.tailscale.com/stable/tailscale-setup-latest-amd64.msi" -OutFile "C:\tailscale.msi"
          Start-Process msiexec -ArgumentList "/i C:\tailscale.msi /quiet /norestart" -Wait

          
          Start-Sleep -Seconds 5
          & "C:\Program Files\Tailscale\tailscale.exe" up --authkey="$Env:TAILSCALE_AUTHKEY" --hostname="github-rdp-server"

          Start-Sleep -Seconds 8

          
          $ts_ip = & "C:\Program Files\Tailscale\tailscale.exe" ip -4

          Write-Host ""
          Write-Host "==========================================" -ForegroundColor Green
          Write-Host "  >>> RDP SERVER IS READY! <<<" -ForegroundColor Cyan
          Write-Host "  Tailscale IP : $ts_ip" -ForegroundColor Yellow
          Write-Host "  Username     : NvdAdmin" -ForegroundColor Yellow
          Write-Host "  Password     : P@ssw0rd1qazXSW@#" -ForegroundColor Yellow
          Write-Host "  >> Open mstsc and connect to: $ts_ip" -ForegroundColor Magenta
          Write-Host "==========================================" -ForegroundColor Green

      - name: 4. Keep Server Alive (48 Hours)
        run: |
          for ($i = 1; $i -le 2880; $i++) {
              Start-Sleep -Seconds 60
              Write-Host "[$i/2880] Server running..."
          }
```

创建好文件之后，点击文件右侧的编辑图标，把对应的工作流配置代码完整粘贴进去（配置代码来源可以参考公开的 GitHub Actions 搭建 Windows 云桌面相关的开源项目），检查无误后提交更改。

[](#第三步：生成-Tailscale-认证密钥 "第三步：生成 Tailscale 认证密钥")第三步：生成 Tailscale 认证密钥
-----------------------------------------------------------------------

回到 Tailscale 网站，点击左侧”设置”，选择”密钥”，点击”生成认证密钥”。这里有几个选项需要注意：

*   **可重复使用**：打开这个开关
*   **短暂（Ephemeral）**：也打开，这意味着设备接入网络使用完毕后会自动从设备列表里清理，避免过期设备堆积
*   **名称描述**：随便填一个方便识别的说明

设置完成后点击”生成密钥”，密钥生成后先不要关闭页面，接下来要用到。

[![](https://cdn.jsdelivr.net/gh/hallteacher/2026-8tuchuang/smjm/20260904170320949.png)
](https://cdn.jsdelivr.net/gh/hallteacher/2026-8tuchuang/smjm/20260904170320949.png)

[](#第四步：把密钥添加到-GitHub-仓库的-Secrets "第四步：把密钥添加到 GitHub 仓库的 Secrets")第四步：把密钥添加到 GitHub 仓库的 Secrets
-----------------------------------------------------------------------------------------------

回到 GitHub 项目页面，点击”设置”，找到”密钥和变量”，进入”Actions”分类，点击”新建仓库密钥”。回到 Tailscale 页面复制刚才生成的密钥，粘贴到 GitHub 的密钥值输入框，名称字段填入一个和工作流配置文件里对应的变量名，点击”添加密钥”完成保存。

```bash
TAILSCALE_AUTHKEY
```

[](#第五步：运行工作流，等待虚拟机自动搭建 "第五步：运行工作流，等待虚拟机自动搭建")第五步：运行工作流，等待虚拟机自动搭建
-----------------------------------------------------------------

密钥配置完成后，回到 GitHub 项目页面，点击”Actions”标签，找到对应的工作流（比如命名为 “Windows Cloud RDP” 之类），点击”Run workflow”手动触发运行。

工作流触发之后，会在后台依次自动完成以下几件事：

1.  **开启远程桌面与防火墙规则**
2.  **创建管理员账号**
3.  **安装并连接 Tailscale**
4.  **启动一个 48 小时的保活脚本**，让这台虚拟机在这个时间窗口内持续保持在线状态

等到第三步（安装并连接 Tailscale）执行完成，就可以尝试远程连接这台虚拟机了。

[![](https://cdn.jsdelivr.net/gh/hallteacher/2026-8tuchuang/smjm/20260904170421454.png)
](https://cdn.jsdelivr.net/gh/hallteacher/2026-8tuchuang/smjm/20260904170421454.png)

[](#第六步：远程桌面连接 "第六步：远程桌面连接")第六步：远程桌面连接
--------------------------------------

打开 Windows 自带的”远程桌面连接”工具，把 Tailscale 分配给这台虚拟机的 IP 地址粘贴到”计算机”地址栏，点击连接。接下来输入 GitHub Actions 日志里生成的账号和密码（这些信息会在工作流运行日志里显示，找到并复制粘贴进对应的输入框）。

系统可能会提示”无法验证远程计算机的身份，是否要继续”，这是正常的安全提示（因为这是自建的虚拟机，没有配置官方证书），点击”是”继续，就能成功进入刚才搭建好的这台云端 Windows 虚拟机了。

[](#实测数据：网速和硬件配置 "实测数据：网速和硬件配置")实测数据：网速和硬件配置
--------------------------------------------

进入虚拟机之后，第一件事是测网速。打开浏览器访问 `fast.com`，测得下载速度达到了 **1.4G（约1400兆）**，随后又用 Speedtest 测了一次，结果更是惊人：**下载速度 4.6G，上传速度 2.6G**，这个上传下载速度已经达到企业级万兆网络的规格水平。

[![](https://cdn.jsdelivr.net/gh/hallteacher/2026-8tuchuang/smjm/20260904170154967.png)
](https://cdn.jsdelivr.net/gh/hallteacher/2026-8tuchuang/smjm/20260904170154967.png)

硬件配置方面，进入系统设置查看详细信息：

*   **CPU**：AMD EPYC 7763，企业级 **64核** 处理器，性能非常强劲
*   **内存**：16GB
*   **系统**：最新版本的 Windows

这个配置组合对多任务挂机、跑复杂自动化脚本来说完全没有压力。

IP 归属地检测显示，这台虚拟机的 IP 落地在美国弗吉尼亚州，属于微软 Azure 原生 IP。因为是公开数据中心机房的 IP 段，风险值相对来说会偏高一些，如果计划用来做一些对 IP 纯净度要求较高的用途，需要提前有这个心理预期。

[](#这台虚拟机适合做什么 "这台虚拟机适合做什么")这台虚拟机适合做什么
--------------------------------------

结合实测的网速和硬件表现，比较适合的使用场景包括：

**自动化脚本长期挂机**：48小时的保活周期加上强劲的多核性能，跑定时任务、数据采集类脚本比较合适。

**离线下载**：千兆级别的带宽表现，用来做大文件的离线下载再转存，效率会非常可观。

**开发测试环境**：需要一个 Windows 图形化环境做软件兼容性测试、或者跑一些只支持 Windows 的工具，这台虚拟机配置完全够用。

[](#写在最后 "写在最后")写在最后
--------------------

这套方案的硬件配置和网速表现确实很亮眼，免费搭建出这样一台高配 Windows 云电脑，技术实现上是可行的。但再强调一次开头提到的点：这本质上是把 GitHub Actions 用在了它并非官方设计支持的用途上，长期稳定性和账号安全性存在不确定因素，建议把它当作一个技术尝试或者短期任务使用，不要过度依赖，更不要用来存放重要数据或者承载关键业务。

* * *

> **版权声明：**  本文为数码解码原创，转载请注明出处。仅供技术交流，请勿用于非法用途。

* * *