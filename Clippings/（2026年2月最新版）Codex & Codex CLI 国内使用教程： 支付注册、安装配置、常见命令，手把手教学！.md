---
title: "（2026年2月最新版）Codex & Codex CLI 国内使用教程： 支付注册、安装配置、常见命令，手把手教学！"
source: "https://www.xiaolincoding.com/other/codex.html"
author:
  - "[[小林coding]]"
published: 2025-11-14
created: 2026-04-07
description: "2025最新实测Codex国内使用教程，包含注册支付、Codex CLI安装配置、模型选择、MCP插件安装、双AI联动等完整流程，帮你快速上手OpenAI专业代码AI工具。"
tags:
  - "clippings"
---
## （2026年3月最新版）Codex & Codex CLI 国内使用教程： 支付注册、安装配置、常见命令，手把手教学！

很多小伙伴让我出一下 codex 的使用文档，我就写了这篇。

首先什么是Codex？ **Codex 是 OpenAI 专门做代码的 AI** 。

![Codex](https://cdn.xiaolincoding.com//picgo/image-20251114123939059.png)

我现在做大项目的时候，遇到复杂 bug，都靠它！

**为什么？**

相比 Claude Code：

- ✅ **细节处理更好** （查 bug 特别准）
- ❌ **但是慢** …特别慢…（所以我一般用 Claude 做日常执行，Codex 专门查 bug）

真实案例：agent 生图对比

比如下面的 agent 生图， **右边的 GPT5（Codex 的模型），一次性出稿特别好** ！

![](https://cdn.xiaolincoding.com//picgo/640-20251114125710792.png)

**左边 Claude** ：

- 生成的图有些细节不对
- 需要多轮调整才能搞定

**右边 GPT5（Codex）** ：

- 一次性生成完美
- 细节处理到位，不用反复改

我现在的使用策略

```
日常执行 → 用 Claude Code（快，理解能力强）
      ↓
遇到复杂 bug → 切换到 Codex（慢，但查得准）
      ↓
细节处理 → 继续用 Codex（一次搞定）
```

**特别是大项目** ：

- 代码量几千行
- bug 藏得很深
- Claude 要找好几轮
- **Codex 一次定位，直接告诉你第几行有问题**

> 💡 **结论** ：Codex 不是 Claude 的替代品，而是完美搭档！

问题来了，怎么才体验 Codex？ **接着往下看！**

## 一、怎么才体验 Codex？

目前 Codex 需要付费才能使用，ChatGPT Plus、Pro、Business 等付费会员都可以使用，这些用户网页版就已经有 Codex 入口：

![](https://cdn.xiaolincoding.com//picgo/image-20251114124719895.png)

目前 Codex 和 Claude Code 一样需要付费才能使用，如果你还是免费用户，可以试试这个一键升级工具（支持微信/支付宝付款）：

> ✅小林亲测有效，点击链接🔗👉： [国内自助升级 ChatGPT Plus 网站](http://getgpt.pro/i/xiaolincoding2)

详细的 ChatGPT Plus 充值教程，我也写过详细的教程： [ChatGPT Plusc充值完全指南](https://xiaolincoding.com/other/chatgpt.html) ，手把手教程，亲测有效！

### Codex 使用场景有哪些？

**三种使用方式：** Codex 网页版、IDE扩展、Codex CLI 终端。

GPT-5-Codex 专为 Codex CLI、Codex IDE 扩展、Codex 云环境和在 GitHub 中工作而构建，还支持多种工具使用。

![](https://cdn.xiaolincoding.com//picgo/image-20251114124641572.png)

**下一步** ：安装 Codex CLI（继续往下看！）

## 二、零代码安装 Codex CLI（提示词大法）

🚀 **重点来了** ：你不需要懂命令行！我把安装步骤都写成提示词了，复制给 AI 就行！

### 为什么要装 CLI 版本？

**CLI = 命令行工具** （听起来很专业，其实就是"高级版软件"）

**为什么不装 IDE 拓展插件版？**

- • ✅ **CLI 功能最全** （可以被其他 AI 调用）
- • ✅ **可以管理 MCP 插件** （给 AI 装"外挂"）
- • ✅ **可以变成 MCP 给其他 AI 用** （后面教你）

**但是！重点来了** ：

你完全不需要懂命令行！我已经把所有步骤都写成提示词了！

### 准备工作：先装个 AI 搭档

我推荐 **[Trae](https://www.trae.com.cn/?utm_source=advertising&utm_medium=xiaolincoding_ug_cpa&utm_term=hw_trae_xiaolincoding)** （中文友好，界面简洁）。

为什么要装这个？因为后面安装 Codex 的时候，你需要一个 AI 来帮你执行命令…

没下载 Trae？下载教程我也给大家写好了：《 [TRAE-AI编程 – 字节跳动推出的免费AI编程工具](https://xiaolincoding.com/other/trae.html) 》

### Codex CLI 安装步骤

#### 第1步：复制这段话，发给 Trae（或其他 AI）

```
帮我自动检查环境并安装 Codex CLI 工具，按以下步骤执行：

第一步：检查系统和环境
- 检查我的操作系统（Mac/Linux/Windows）
- 如果是 Windows：检查是否有 WSL（运行 wsl --version 或 wsl -l -v）

第二步：检查 Node.js
- 运行 node -v 检查 Node.js 是否已安装
- 如果没有安装，提示我：
  Mac: 运行 brew install node 或去 nodejs.org 下载
  Linux: 运行 sudo apt install nodejs npm 或去 nodejs.org 下载
  Windows: 去 nodejs.org 下载安装

第三步：安装 Codex
根据环境选择：
- Mac/Linux：直接运行 npm install -g @openai/codex
- Windows 有 WSL：在 WSL 环境运行 npm install -g @openai/codex
  （提醒我：以后使用时先输入 wsl 再输入 codex）
- Windows 无 WSL：先询问我是否要安装 WSL（推荐，更稳定）
  - 如果要：运行 wsl --install，提醒我重启后继续
  - 如果不要：运行 npm install -g @openai/codex --force --no-os-check
    （警告：Windows 原生环境可能有兼容问题）

第四步：验证安装
- 运行 codex --version 检查是否安装成功
- 告诉我下一步该怎么启动 Codex
```

#### 第2步：等 AI 自动帮你装

执行上面的这段话后，AI 会自动检查你的系统、安装依赖、安装 Codex…你只需要坐着等！

如果你是极客，就是想自己手动执行命令安装的话，可以按下面的步骤（注意：已经让AI 自动帮你安装的同学，不需要看这个手动安装的命令）：

```bash
# 1. 确保 Node ≥ 22
node -v   # v22.5.1

# 2. 一行命令搞定
npm i -g @openai/codex

# 3. 验证
codex --version   # 0.36.0

如果感觉国内 NPM 很慢？两条路：
1. \`npm i -g @openai/codex --registry=https://registry.npmmirror.com\`
2. 或者 \`brew install codex\`（for mac 用户，Homebrew 已同步最新版）
```

#### 第3步：登录你的 ChatGPT 账号

安装完成后，第一次进入 Codex 会要求登录。

![img](https://cdn.xiaolincoding.com//picgo/640-20251114130210731.png)

用刚才买的 Google 账号登录就行！

#### 第4步：后续启动（超简单）

打开终端，输入 `codex` ，回车！

![img](https://cdn.xiaolincoding.com//picgo/640-20251114130214283.png)

看到这个对话框了吗？ **成功了！**

**遇到问题怎么办？**

- • 卡住不动？等3分钟，可能在下载依赖
- • 报错了？截图发给 AI，让它帮你解决

> 💡 **记住** ：不要自己动手敲命令，让 AI 帮你！

## 三、基础操作（5分钟上手）

### 1\. 拖拽文件（有个坑，别踩）

**❌ 错误方法** ：直接把文件拖进去 → 失败！

**✅ 正确方法** ： **按住 Shift** ，再拖进去 → 成功！

> 💡 **为什么？** 因为 Codex 需要 Shift 键才能识别拖拽…我也不知道为什么要这么设计…

### 2\. 选模型（推荐 gpt-5 high）

输入 `/model` ，回车。

![img](https://cdn.xiaolincoding.com//picgo/640-20251114130221659.png)

**两个模型的区别** ：

- • **codex 专业版** ：纯代码生成（速度快，但理解能力弱）
- • **gpt-5 通用版** ：理解能力强（推荐新手用这个！）

![img](https://cdn.xiaolincoding.com//picgo/640-20251114130224823.png)

选档次的时候，当然选 **high** ！

- • **high** = 高推理能力（处理复杂问题更准）
- • 缺点：稍微慢一点，但值得！

![img](https://cdn.xiaolincoding.com//picgo/640-20251114130228244.png)

### 3\. 权限设置（推荐"自动判断"）

输入 `/` ，选 `approvals` 。

![img](https://cdn.xiaolincoding.com//picgo/640-20251114130231858.png)

**三种权限模式** ：

| 权限 | 读文件 | 改文件 | 适合谁？ |
| --- | --- | --- | --- |
| 只读 | ✅ | ❌ | 超级谨慎（但啥也干不了…） |
| **自动判断** | ✅ | 需确认 | **新手首选！** |
| 全通过 | ✅ | ✅ | 老手（有风险） |

**为什么选"自动判断"？**

- AI 读文件 → 自动通过（不用每次点确认，省事！）
- AI 改文件 → 弹窗确认（重要操作你说了算）

![img](https://cdn.xiaolincoding.com//picgo/640-20251114130235629.png)

### 4\. 其他常用命令

**新建会话** ： `/new`

![img](https://cdn.xiaolincoding.com//picgo/640-20251114130242810.png)

**让 AI 理解你的项目** ： `/init`

![img](https://cdn.xiaolincoding.com//picgo/640-20251114130246644.png)

这个命令会生成一个 `.claude.md` 配置文件，下次打开项目 AI 就自动知道这是啥了！

**查看已安装的 MCP** ： `/mcp`

![img](https://cdn.xiaolincoding.com//picgo/640-20251114130249961.png)

> 💡 **记住这4个操作** ，基本够用了！

## 四、给 AI 装插件（MCP 管理，又是提示词大法）

🔥 **又一个爆点** ：别的教程让你手改配置文件，我们用一句话搞定！

### MCP 是啥？

**MCP = 给 AI 装插件**

**举个例子** ：

- • 默认情况：AI 只能写代码、读文件
- • 装了 **Chrome DevTools MCP** → AI 可以操作浏览器！（自动测试、爬虫、截图）
- • 装了 **滴滴出行 MCP** → AI 可以帮你叫车！（是的，真的可以）

### 怎么装？（提示词大法好）

#### 第1步：复制这段提示词，发给 Codex

```
帮我管理 MCP 服务(添加或删除)。

我会提供配置信息,格式如下:
{
  "mcpServers": {
    "服务名": {
      "command": "命令",
      "args": ["参数列表"]
    }
  }
}

请你根据我的需求:

## 添加服务
1. 提取配置中的服务名、command、args
2. 转换成命令:codex mcp add-json <服务名> '{"command": "xxx", "args": [...]}'
3. 执行安装
4. 安装完成后测试是否可用

## 删除服务
使用命令:codex mcp remove <服务名>
```

#### 第2步：告诉 Codex 你要装什么

例如：

```
@提示词

添加 MCP:
{
  "mcpServers": {
    "chrome-devtools": {
      "command": "npx",
      "args": ["chrome-devtools-mcp@latest"]
    }
  }
}
```

**就这么简单！** AI 会自动帮你装好！

**验证** ：

输入 `/mcp` ，看到 “chrome-devtools” 出现在列表里就成功了！

> 💡 **提示词大法** ：所有复杂操作，都可以让 AI 帮你搞定！

## 五、终极玩法 – 双 AI 联动（省钱又爽）

💡 **最后一个爆点** ：让 Claude Code 当项目经理，Codex 当技术专家！

### 什么意思？

简单说： **在 Claude Code 里装一个 Codex 插件，遇到复杂代码问题自动调用 Codex！**

**工作流程** ：

```
你提问 → Claude Code 开始干活
       → 遇到复杂 bug（查不出来）
       → 自动调用 Codex MCP
       → Codex 返回精准答案
       → Claude Code 继续完成任务
```

**你完全不用切换工具！一切自动完成！**

### 为什么要这么做？

**问题场景** ：

- • 你主要用 Claude Code（快，理解能力强）
- • 但 Claude 处理复杂代码细节不如 Codex
- • 你又买了便宜的 Team 账号（10元/月）

**解决方案** ： 把 Codex 装成 Claude Code 的"外挂"！

- • 日常工作用 Claude Code（架构设计、多轮对话）
- • 遇到技术难题 → 自动调用 Codex（查 bug、代码细节）

**特别适合国产模型用户！** 如果你用 GLM 之类的，配合 Codex 简直完美！

### 安装步骤

**复制这段话，发给 Claude Code（或其他 AI）** ：

```
用下述指令，安装 codex MCP:

claude mcp add codex -s user -- codex -m gpt-5-codex -c model_reasoning_effort="high" mcp

安装成功后，测试是否正常显示
```

**验证一下** ：

在 Claude Code 里输入 `/mcp` ，看到 “codex” 出现在列表里就成功了！

### 为什么推荐双 AI 联动？

| AI | 擅长什么？ | 怎么用？ |
| --- | --- | --- |
| **Claude Code** | 理解项目、架构设计、多轮对话、日常执行 | **主力** |
| **Codex** | 查 bug、代码细节、复杂逻辑 | **辅助** |

**结论** ：取长补短，省钱又高效！

## 六、快捷键速查表（收藏备用）

### 常用快捷键

| 作用 | Mac | Windows/Linux |
| --- | --- | --- |
| **多行输入** | `Option + Enter` | `Alt + Enter` |
| **中断响应** | `Ctrl + C` | `Ctrl + C` |
| **历史命令** | `↑ / ↓` | `↑ / ↓` |

### 编辑快捷键

| 作用 | Mac | Windows/Linux |
| --- | --- | --- |
| 跳到行首 | `Ctrl + A` | `Ctrl + A` |
| 跳到行尾 | `Ctrl + E` | `Ctrl + E` |
| 按词移动 | `Option + ←/→` | `Alt + ←/→` |
| 删到行首 | `Ctrl + U` | `Ctrl + U` |
| 删到行尾 | `Ctrl + K` | `Ctrl + K` |
| 删除单词 | `Ctrl + W` | `Ctrl + W` |
| 撤销 | `Ctrl + /` | `Ctrl + /` |

**有问题评论区见！**

评论加载失败