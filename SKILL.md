---
name: gpt-image-skills-pack
description: 当用户想做小红书封面和图文、电影海报、动态表情包、微信红包封面、宠物新年写真或书页电影海报时使用：安装 VaneAi888 开源的六个 GPT Image 2.6 生图 Skill，按选定的风格和版式出图。需要 AI Agent 有生图能力。
---

# Vane GPT Image Skills 合集

一键安装 6 个开源 GPT Image 2.6 生图 Skill，覆盖小红书图文和电影海报，也能做动态表情包、微信红包封面、宠物写真和书页海报。每个 Skill 都是一份完整的生图 SOP，Agent 读了就能按选定的风格和版式出图。仓库 [VaneAi888/vane-gpt-image-skills](https://github.com/VaneAi888/vane-gpt-image-skills)，MIT 许可证，1300+ Star。

## 触发

用户想做小红书封面和图文、电影海报，或者要做动态表情包、微信红包封面、宠物新年写真、书页海报时使用。

## 硬性规则

- 生成图片需要 AI Agent 有生图能力（GPT Image 2.6 或同类模型），没有生图工具时只能输出提示词和版式说明。
- 用户的照片只在当次会话中使用，不上传到外部服务、不加入发布包。
- 效果图是 AI 生成的示例，图中出现的产品名、书名和人物不代表官方合作。

## 安装

```bash
git clone https://github.com/VaneAi888/vane-gpt-image-skills.git
cd vane-gpt-image-skills
python3 scripts/install_skills.py --all
```

安装后开启新对话，用 `$Skill名` 调用。只装某一个：`python3 scripts/install_skills.py --skill vane-xhs-design`（`--list` 看全部名字）。更新已安装的：`python3 scripts/update_skills.py`。

默认装到 `~/.codex/skills/`。用的是别的 AI Agent 时，装完把这几个文件夹复制到它的 Skill 目录。已有同名 Skill 时安装器会停下、不覆盖，`--all` 任一个已存在就全部不装，所以先 `ls ~/.codex/skills/` 看一眼，已装的改用单装或更新脚本。安装器不装 Pillow、FFmpeg 这类依赖，做 GIF 表情包要另外装好。

## 6 个 Skill 一览

| Skill 名 | 做什么 | 用法示例 |
| --- | --- | --- |
| `vane-xhs-design` | 小红书封面和正文图，2 种风格：手帐拼贴风、极简产品风 | `$vane-xhs-design 手帐拼贴风，把下面的文字做成一套图文` |
| `vane-cinematic-poster` | 电影级海报，36 种构图版式，支持中英文 | `$vane-cinematic-poster 用版式 03 做一张竖版海报` |
| `vane-portrait-gif-stickers` | 照片转 12 种画风的动态表情包，默认一套 16 张 GIF | `$vane-portrait-gif-stickers Q版萌系，用这张照片` |
| `vane-book-cinema` | 把一本书变成电影感海报 | `$vane-book-cinema 《三体》` |
| `wechat-red-packet-cover` | 微信红包封面，36 种风格 | `$wechat-red-packet-cover 传统艺术风格` |
| `vane-pet-new-year-portrait` | 宠物新年写真，4 种场景 | `$vane-pet-new-year-portrait 红色背景` |

## 小红书图文的制作流程（以手帐拼贴风为例）

1. 给 Agent 文字内容和要用的风格（手帐拼贴风或极简产品风）
2. Agent 先给出九宫格预览和每页文案
3. 确认后逐张生成独立图片（九宫格只是预览，不能当九张成图用）
4. 配图可以用自己的照片、截图，也可以让 Agent 生成 AI 配图

## 输出格式

每个 Skill 输出独立的 PNG/JPG 图片。表情包额外输出 320×320 透明背景 GIF 和 ZIP 打包。海报默认竖版 2:3。
