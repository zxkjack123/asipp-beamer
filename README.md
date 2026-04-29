# 中科院等离子体物理研究所 Beamer 模板

与 `ai-ppt` MCP 服务器中的 `asipp` PPTX 模板视觉对齐的 Beamer 主题。
2026-04 重写，配色与版式参照 `ai_ppt/templates/asipp_template.pptx` 母版。

## 视觉特征

- 16:9 白底 + 深藏青文字（来自 PPTX `theme1.xml`）
- ASIPP "CQ" logo 置于每页左上角
- 标题下方一道细蓝线分隔（`#6096E6`）
- 右下角页码 `第 N / M 页`（可切换为英文 `Page N of M`）
- 章节分隔页：上下两条蓝线 + 居中大字章节名（对应 PPTX layout 4 `1_节标题`）
- 专用结束页 `\thankspage{...}`（对应 PPTX layout 12 `末尾幻灯片`）

## 调色板

| 色名 | HEX | 用途 |
|------|------|------|
| `ASIPPNavy` | `#0F1423` | 标题、正文 |
| `ASIPPBlue` | `#6096E6` | 标题分隔线、bullet、block 标题 |
| `ASIPPBlueDark` | `#0563C1` | 副标题、强调 |
| `ASIPPCyan` | `#58B6E5` | 次要强调 |
| `ASIPPGreen` | `#56CA95` | example block |
| `ASIPPAmber` | `#FFBA55` | 子项 bullet、辅助强调 |
| `ASIPPSalmon` | `#F18870` | 备用 |
| `ASIPPRed` | `#EC5F74` | alert text、alertblock |

## 使用

把仓库 4 个 `.sty` 文件以及 `asipp_logo.pdf` 放到工作目录或 TeX 搜索路径，然后：

```latex
\documentclass[aspectratio=169]{ctexbeamer}   % 中文
% \documentclass[aspectratio=169]{beamer}    % 英文
\usetheme{ASIPP}                              % 默认白底（推荐，与 PPTX 一致）
% \usetheme[dark]{ASIPP}                     % 暗色变体（屏显场景）

\title{演示文稿标题}
\subtitle{副标题}
\author{报告人}
\institute{中国科学院等离子体物理研究所}
\date{\today}

\begin{document}
\frame[plain,noframenumbering]{\titlepage}

\section{第一部分}
% 自动插入章节分隔页

\begin{frame}{要点列表}
  \begin{itemize}
    \item 第一点
    \item 第二点
  \end{itemize}
\end{frame}

\thankspage[Q\&A]{谢谢！}
\end{document}
```

中文请使用 `xelatex` 编译。

## 主题选项

| 选项 | 默认 | 作用 |
|------|------|------|
| `dark` | off | 切换为暗色（深藏青底）变体 |
| `white` | on | 显式选择白底（默认即此） |
| `nologo` | off | 隐藏所有页面的 logo |
| `compactlogo` | off | 标题页 logo 缩小 |
| `nav` | off | 显示 beamer 导航按钮 |
| `noslidenumbers` | off | 隐藏页码 |
| `sections` | off | 标题栏右侧显示当前章节名 |
| `nosectionpage` | off | 禁用 `\section` 触发的自动章节分隔页 |

## 提供的命令

| 命令 | 说明 |
|------|------|
| `\asippsectionpage` | 手动插入章节分隔页 |
| `\thankspage[副标题]{主消息}` | 末尾致谢页 |
| `\asippfootenglish` | 切换页码为 `Page N of M` |
| `\asippfootchinese` | 切换回 `第 N / M 页`（默认） |

## 文件清单

| 文件 | 内容 |
|------|------|
| `beamerthemeASIPP.sty` | 主题入口、选项处理、标题页/章节页/末尾页模板 |
| `beamercolorthemeASIPPWhite.sty` | 白底配色（默认） |
| `beamercolorthemeASIPP.sty` | 暗色配色 |
| `beamerouterthemesubtle.sty` | frametitle 栏 + footline |
| `asipp_logo.pdf` | 所标志（请确认使用权限） |
| `demo.tex` / `demo.pdf` | 视觉对齐演示 |

## 历史

最初版本（2010s）改自 [travitch/uw-beamer-template](https://github.com/travitch/uw-beamer-template)，
当时只替换了 logo，配色仍是 Beamer crane 风格（暗红 + 土金）。

2026-04 全部重写以对齐 `ai-ppt` MCP 服务器的 `asipp` PPTX 模板视觉规范，
LaTeX/Beamer 与 PowerPoint 输出现可保持一致风格。

意见反馈：zhangxk@ipp.ac.cn 或 GitHub Issues。
