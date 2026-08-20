---
up: "[[我的产品管理，开发，上线，圈子]]"
related: []
tags: [参考资料, AI, OPC, WorkBuddy, 白皮书, 排版]
日期: 2026-08-21
来源: 腾讯云 WorkBuddy 团队
---

# WorkBuddy OPC 白皮书

> [!info] 元信息
> - **标题**：WorkBuddy OPC 白皮书 — AI 时代一人公司的商业与技术重构
> - **副题**：从超级个体到超级团队
> - **出品**：腾讯云 WorkBuddy 团队
> - **日期**：2026 年 6 月
> - **规模**：110 页 A4，约 3.8 MB（PDF）
> - **来源 URL**：`workbuddy-space-static.codebuddy.work/.../opc-whitepaper-mobile.html`
> - **本地副本**：PDF + 原始 HTML 已存至 `附件/`

## 一、6 章内容结构（目录）

| 章 | 标题 | 核心内容 |
|---|---|---|
| 1 | 时代浪潮：OPC 正在重塑创业版图 | 规模数据、超级个体定义、效率革命、Polsia、AI 原生三个陷阱 |
| 2 | 范式转移：从「雇人」到「调度算力」 | 硅基员工、80/20 范式、三层能力模型、六大商业模式、C 端赛道、万能套利公式 |
| 3 | 中国机遇：政策、园区与本地化生态 | 北京朝阳、深圳、20+ 省市密集政策、园区与本地化生态 |
| 4 | WorkBuddy 解法：从一人公司到超级团队 | 团队必要性、组织竞争力公式、三种超级团队形态、三层产品架构、混合架构最优解 |
| 5 | 实战图鉴：OPC × WorkBuddy 的 N 种打开方式 | 全流程解决方案、用户案例 |
| 6 | 共建生态：OPC 生产基础设施的建设路径 | 四个建设维度、认证体系、合作形式 |

## 二、核心数据点（书内高亮）

- 中国一人有限责任公司存量：**突破 1,600 万家**（截至 2025 年底），占全国企业总量约 **27.4%**
- 2025 上半年新增 286 万户，同比 **+47%**，占新注册企业 23.8%
- 主动立信一人公司：近 **570 万家**（截至 2026.5），同比 **+42%**
- 90 后/00 后创业者占新注册企业近 **1/4**

> 对用户的意义：用户本人就是 OPC（律师执业 + AI 副业），这份白皮书既是"趋势确认"，也是"同行画像"。

## 三、这本书的排版是怎么做出来的？

> 回应原话：这种白皮书是怎么做出这种书本排版的，太好看了。

### 1. 核心思路：HTML + CSS 做"书"，不是 Word/PPT

它不是用 Word/InDesign/Canva 做的——而是一个**单文件 HTML**（约 290 KB），用网页技术模拟出书本级排版。这是"PDF Native"思路的现代版本：代码即设计稿。

### 2. 关键技术栈（从源码反推）

| 层 | 做法 | 说明 |
|---|---|---|
| 结构 | 110 个 `<div class="page">` 容器 | 每个宽 210mm × 高 297mm = **精确 A4 物理尺寸** |
| 分页 | `page-break-after: always` + `@page { size: A4; margin: 0 }` | 浏览器打印 / PDF 输出严格按 A4，每页独立 |
| 样式 | 全部 CSS 内联在 `<style>` | 无 Tailwind 编译痕迹，无外部框架 |
| 资源 | 图片 base64 内嵌（1 张 logo） | 字体用系统栈 `-apple-system, 'PingFang SC', 'Microsoft YaHei'`，不依赖网络字体 |
| 装饰 | `linear-gradient` + `clip-path` + `::before/::after` 伪元素 | 封面光带、章节底色条、品牌色贯穿 |
| 主色 | `#1DB886`（WorkBuddy 品牌绿） | 标题、强调、装饰条、按钮全统一 |

### 3. 关键 CSS 模板（可复用的"书本级排版"骨架）

```css
@page { size: A4; margin: 0; }
* { box-sizing: border-box; margin: 0; padding: 0; }
body {
  font-family: -apple-system, 'PingFang SC', 'Microsoft YaHei', 'Noto Sans SC', sans-serif;
  font-size: 11pt;
  line-height: 1.8;
  color: #1a1a1a;
  background: #fff;
}

.page {
  width: 210mm;
  height: 297mm;
  position: relative;
  overflow: hidden;
  page-break-after: always;   /* 核心：每页独立 */
  background: #fff;
}
.page:last-child { page-break-after: auto; }

/* 封面装饰光带 */
.cover::before {
  content: '';
  position: absolute;
  top: 0; right: 0;
  width: 120mm;
  height: 100%;
  background: linear-gradient(160deg, rgba(46,207,171,.08) 0%, rgba(29,184,134,.02) 100%);
  clip-path: polygon(30% 0, 100% 0, 100% 100%, 0 100%);
}
.cover::after {
  content: '';
  position: absolute;
  bottom: 0; left: 0;
  width: 100%;
  height: 4px;
  background: linear-gradient(90deg, #1DB886, #2ECFAB);
}
```

### 4. 工具推测（这种一致性纯手写很难做到）

| 可能性 | 概率 | 说明 |
|---|---|---|
| Figma → Anima / Figma-to-HTML 插件导出 | 高 | 设计师出稿，工具直接转 HTML |
| Webflow / Framer 类可视化建站但导出干净 HTML | 高 | 模板多、品牌站常见做法 |
| 腾讯内部设计系统 + 自研 HTML 模板引擎 | 中 | 腾讯品牌一致性最强的解释 |
| 基于 Puppeteer/Playwright 的 PDF 流水线 | 中 | 内容数据 + 模板代码生成 |

### 5. 想要自己做这种白皮书，最快路径

| 你的诉求 | 推荐工具 | 备注 |
|---|---|---|
| 不想碰代码 | [Canva Docs](https://www.canva.com/docs/)、[typedream](https://typedream.com/)、[Pagegen](https://pagegen.tech/)、[Notion + Super](https://super.so/) | 直接拖拽，导出 PDF / 网页 |
| 想深度定制样式 | Figma 设计 + 上面 CSS 模板 + Chrome 无头打印 PDF | 推荐路径，最自由 |
| 数据驱动（多份、自动化） | React + @react-pdf/renderer，或 Vue + html2pdf | 适合"客户/产品/团队"各出一份白皮书 |

> 实操笔记：本次就是用 **macOS Chrome 无头打印** 把 HTML 转成 PDF 保进 Obsidian 的。命令：
> `/Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --headless --no-pdf-header-footer --print-to-pdf=out.pdf file://xxx.html`

## 四、嵌入 PDF 阅读

> Obsidian 原生支持 PDF 内联预览（懒加载，翻页体验良好）。

![[WorkBuddy-OPC白皮书.pdf]]

> 阅读小贴士：在 Obsidian 打开此笔记后，PDF 块右上角的"..."可以跳到指定页码。

## 五、文件清单

| 文件 | 位置 | 大小 | 用途 |
|---|---|---|---|
| 完整白皮书 PDF | `附件/WorkBuddy-OPC白皮书.pdf` | 3.8 MB | 阅读主载体 |
| 原始 HTML（含 CSS 源码） | `附件/opc-whitepaper-mobile.html` | 293 KB | 学习排版、可二次改造 |
