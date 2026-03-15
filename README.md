# Tailor Resume for Trae

> 把多版本简历和一个或多个 JD，整理成真正为目标岗位定制的 Word 简历。

## 这是什么？

这是一个给 **Trae IDE** 用的简历定制技能（skill）。

你可以把自己不同阶段、不同方向、不同版本的简历一起交给它，再把一个或一批目标岗位 JD 丢进去。它会先把所有简历内容整理成一个完整的"经历池"，再对照 JD 找 gap、主动追问你可能遗漏但其实做过的经历，最后按具体岗位重写简历，并输出可继续编辑的 Word 文档。

它不是简单地"改几个关键词"，而是把"多版本简历整理 + 批量 JD 分析 + gap 挖掘 + 针对性改写 + Word 输出"串成一个完整流程。

---

## 核心能力

### 1. 多版本简历 → 经历池

你可以把所有版本的简历一起喂进去。无论是早期版本、不同岗位方向版本，还是某一版里写过后来删掉的内容，它都会统一提取出经历、项目、技能和成果，合并成一个完整的经历池。

### 2. 批量喂入 JD

你可以一次性丢给它多个 JD。支持文本、文件、链接、截图，甚至把 10 个岗位的 JD 截图丢进同一个文件夹里，它也会逐个读取、逐个分析。

### 3. 挖掘 gap 经历

它会把经历池和 JD 逐项对比，找出中间的 gap，然后主动问你问题。很多时候不是你没做过，而是你没想到这段经历可以写进这个岗位的简历里。它会帮你把这些可用但没写出来的经历挖出来。

### 4. 针对 JD 润色改写

它会按 STAR 原则重写你的经历，但不是模板式套话。它会根据这个具体 JD 调整侧重点、换用更贴近岗位需求的表达和关键词，让招聘方更快看出"你做过他们要的事情"。

### 5. 保留排版，输出 Word

最后它会输出 Word 文档。如果你有多个版本的 `.docx` 简历，还可以指定最喜欢的一份作为样式参考，让新简历继续沿用原来的字体、间距、页边距和整体版式。

---

## 安装方法

### 第一步：确认你已经安装了 Trae IDE

如果你还没有安装 Trae，请先去官网下载安装：
- Trae 官网：[trae.ai](https://trae.ai/)

安装完成后，打开 Trae IDE，确保能正常使用。

### 第二步：安装这个技能

有两种安装方式，选一种你喜欢的：

#### 方式一：手动安装（推荐新手使用）📁

**步骤 1：下载文件**

1. 点击这个页面右上角的绿色按钮 `Code`
2. 选择 `Download ZIP` 下载压缩包
3. 解压后，你会看到一个叫 `tailor-resume` 的文件夹

**步骤 2：找到 Trae 的技能目录**

Trae 的技能存放在你项目的 `.trae/skills/` 目录下。

**步骤 3：复制文件夹**

把解压出来的 `tailor-resume` 文件夹复制到你的项目的 `.trae/skills/` 目录里。

最终目录结构应该是这样的：

```
你的项目/
└── .trae/
    └── skills/
        └── tailor-resume/
            ├── SKILL.md
            └── md_to_docx.py
```

**步骤 4：重启 Trae**

关闭并重新打开 Trae IDE，或者在项目中重新加载。

---

#### 方式二：命令行安装（适合熟悉终端的用户）🚀

打开终端（命令行），进入你的项目目录，然后执行：

```bash
# 创建目录
mkdir -p .trae/skills

# 克隆仓库
git clone https://github.com/rongmiao926-hub/trae-tailor-resume-skill.git temp-clone

# 复制技能文件夹
cp -r temp-clone/tailor-resume .trae/skills/

# 清理临时文件
rm -rf temp-clone
```

Windows PowerShell 用户：

```powershell
# 创建目录
New-Item -ItemType Directory -Force -Path .trae\skills

# 克隆仓库
git clone https://github.com/rongmiao926-hub/trae-tailor-resume-skill.git temp-clone

# 复制技能文件夹
Copy-Item -Recurse -Force temp-clone\tailor-resume .trae\skills\

# 清理临时文件
Remove-Item -Recurse -Force temp-clone
```

---

### 第三步：安装依赖（可选但推荐）

为了让简历输出效果更好，建议安装 `python-docx`：

```bash
pip install python-docx
```

如果你已经安装了 pandoc，也可以用它来生成 Word 文档（效果会更好）。

---

## 使用方法

安装好之后，在 Trae 里直接跟它说话就行，不需要背任何命令。

### 基础用法

直接告诉它你的简历在哪、JD 是什么：

```
帮我用 tailor-resume 改简历。我的简历放在 F:\Documents\简历库\，JD 如下：

[粘贴 JD 内容]
```

### 从 URL 获取 JD

```
帮我用 tailor-resume 改简历。简历在 F:\Documents\resumes\，JD 链接是 https://example.com/job/12345
```

### 批量处理多个 JD

```
帮我用 tailor-resume 改简历。我有多个岗位要投，简历在 F:\Documents\resumes\，JD 截图都在 F:\Documents\jd-screenshots\。请先统一分析 gap，再分别生成每个岗位的定制简历。
```

### 指定样式参考

```
帮我用 tailor-resume 改简历。我的简历在 F:\Documents\resumes\，并且请沿用 F:\Documents\resumes\终版简历.docx 的排版风格。JD 如下：...
```

---

## 支持的文件格式

### 简历格式
- ✅ Word 文档（.docx, .doc）
- ✅ PDF 文档（.pdf）
- ✅ Markdown 文档（.md）
- ✅ 纯文本文件（.txt）

### JD 输入方式
- ✅ 直接粘贴文本
- ✅ 本地文件（支持上述所有格式）
- ✅ 网页链接（URL）
- ✅ 截图或图片
- ✅ 批量文件（整个文件夹）

---

## 常见问题

### Q：我只提供 PDF 简历可以吗？

A：可以提取内容，但通常无法完整复用原排版。建议至少提供一份 `.docx` 简历作为样式参考。

### Q：JD 网页打不开怎么办？

A：如果网页需要登录或有反爬虫机制，请直接复制粘贴 JD 文本，或者保存为本地文件。

### Q：生成的简历在哪里？

A：简历会生成在你提供的简历目录下，文件名格式为 `简历_<岗位名称>.docx`。

### Q：支持英文简历吗？

A：目前主要针对中文简历优化。如果你需要英文版本，可以在对话中明确说明。

---

## 项目结构

```
tailor-resume/
├── SKILL.md        # 技能主文件，定义了工作流程和规则
└── md_to_docx.py   # Markdown 转 Word 的辅助脚本
```

---

## 反馈与贡献

如果你在使用过程中遇到问题，或者有改进建议，欢迎：
- 在 GitHub 上提 Issue
- 提交 Pull Request

---

## 许可证

MIT License
