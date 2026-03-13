# Notion Style — Obsidian Theme

将 Obsidian 的界面全面改造为 Notion 风格的主题，支持亮色/暗色模式切换，兼容桌面端与移动端。

---

## 视觉效果预览

| 元素 | Notion 风格表现 |
|------|----------------|
| **标题** | H1 40px → H6 16px 字体梯度，加粗层级清晰 |
| **代码块** | 灰色背景 `#f7f6f3`，3px 圆角，等宽字体 |
| **内联代码** | 浅灰背景 + 红色文字，紧凑圆角 |
| **列表** | 三级嵌套符号（● ◦ ▪），任务列表蓝色复选框 |
| **Callout** | 蓝/绿/黄/红四色系，左侧彩色边框 |
| **表格** | 灰色表头，细边框，hover 高亮行 |
| **页面边距** | 桌面端 96px，移动端自动收窄 |

---

## 文件结构

```
notion-style/
├── manifest.json   # 主题元数据（Obsidian 必需）
├── theme.css       # 全量样式文件（含颜色变量 + 所有组件）
└── README.md       # 本文件
```

---

## 安装方法

### 方法一：手动安装（推荐）

1. 找到你的 Obsidian Vault 目录。
2. 进入 `<你的Vault>/.obsidian/themes/` 文件夹（若不存在请手动创建）。
3. 在 `themes/` 目录下新建一个文件夹，命名为 `Notion Style`。
4. 将 `manifest.json` 和 `theme.css` 两个文件复制进去。

   最终结构如下：
   ```
   <你的Vault>/
   └── .obsidian/
       └── themes/
           └── Notion Style/
               ├── manifest.json
               └── theme.css
   ```

5. 打开 Obsidian → **设置 → 外观 → 主题**，在列表中选择 **Notion Style**，点击应用即可。

### 方法二：一键脚本安装

在终端中执行以下命令，将 `YOUR_VAULT_PATH` 替换为你的 Vault 实际路径：

```bash
VAULT="YOUR_VAULT_PATH"
DEST="$VAULT/.obsidian/themes/Notion Style"
mkdir -p "$DEST"
cp /path/to/this/folder/manifest.json "$DEST/"
cp /path/to/this/folder/theme.css     "$DEST/"
echo "✅ 安装完成，请在 Obsidian 设置 → 外观 中选择 Notion Style"
```

---

## Callout 使用方法

在笔记中使用以下语法来创建 Notion 风格的提示框：

```markdown
> [!info] 信息提示
> 这是一条蓝色的信息提示，用于说明性内容。

> [!tip] 小贴士
> 这是一条绿色的建议或技巧。

> [!warning] 注意
> 这是一条黄色的警告，需要引起注意。

> [!danger] 危险
> 这是一条红色的错误或危险提示。

> [!quote] 引用
> 这是一段引用内容。

> [!note]- 可折叠标注（默认收起）
> 点击标题可展开。
```

支持的 Callout 类型：

| 类型关键词 | 颜色 | 用途 |
|-----------|------|------|
| `info`, `note` | 蓝色 | 说明、信息 |
| `tip`, `success`, `done`, `check` | 绿色 | 建议、成功 |
| `warning`, `caution`, `attention` | 黄色 | 警告、注意 |
| `danger`, `error`, `bug`, `failure` | 红色 | 错误、危险 |
| `quote`, `cite`, `example` | 灰色 | 引用、示例 |

---

## 颜色系统（CSS 变量速查）

所有颜色均定义为 CSS 变量，可在 `theme.css` 顶部自定义。

### 亮色模式

| 变量名 | 默认值 | 用途 |
|--------|--------|------|
| `--notion-bg-primary` | `#ffffff` | 页面背景 |
| `--notion-bg-secondary` | `#f7f6f3` | 侧边栏/代码块背景 |
| `--notion-text-primary` | `#37352f` | 主文字 |
| `--notion-text-secondary` | `#787774` | 次要文字 |
| `--notion-text-link` | `#2382e2` | 链接颜色 |
| `--notion-border` | `rgba(55,53,47,0.16)` | 边框 |
| `--notion-code-text` | `#eb5757` | 内联代码文字 |

### 暗色模式

| 变量名 | 默认值 | 用途 |
|--------|--------|------|
| `--notion-bg-primary` | `#191919` | 页面背景 |
| `--notion-bg-sidebar` | `#202020` | 侧边栏背景 |
| `--notion-text-primary` | `rgba(255,255,255,0.81)` | 主文字 |
| `--notion-codeblock-bg` | `#2f3437` | 代码块背景 |

---

## 自定义颜色（高级）

如需修改配色，打开 `theme.css`，找到第 1 节 **DESIGN TOKENS**，直接编辑对应变量值即可，无需修改其他任何地方。

```css
/* 示例：将亮色模式背景改为暖白色 */
.theme-light {
  --notion-bg-primary: #fefdf9;
}

/* 示例：将链接颜色改为紫色 */
.theme-light {
  --notion-text-link: #7c4dff;
}
```

---

## 兼容性

- **Obsidian 最低版本**：1.0.0
- **支持模式**：实时预览（Live Preview）、阅读视图（Reading View）、源码模式（Source Mode）
- **支持平台**：macOS、Windows、Linux、iOS、Android

---

## 已知问题 & FAQ

**Q: 主题安装后没有变化？**
A: 请确认文件夹名称为 `Notion Style`（区分大小写），且文件夹内同时包含 `manifest.json` 和 `theme.css`。

**Q: 代码块没有语法高亮？**
A: 主题提供基础的 token 颜色，完整语法高亮依赖 Obsidian 内置的 Prism.js。在实时预览模式下高亮效果最佳。

**Q: 如何恢复默认样式？**
A: 在 Obsidian 设置 → 外观 → 主题中，选择 **Default** 即可。

**Q: 可以和 Style Settings 插件配合使用吗？**
A: 目前不支持 Style Settings 面板，但可以直接编辑 `theme.css` 中的 CSS 变量进行自定义。

---

## 版本历史

| 版本 | 日期 | 变更 |
|------|------|------|
| 1.0.0 | 2026-03-13 | 首次发布，完整 Notion 风格实现 |
