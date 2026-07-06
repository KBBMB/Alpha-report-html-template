# HTML 公司报告模板规范（16:9）

> 这个 skill 的主规则来源文件同步自 `..\\html-company-report-style-spec.md`。
> 如需改版式、slide 类型、logo 尺寸、图表样式，先改这里的规则认知，再同步 demo。

## 核心定位

这不是长滚动网页，而是一套按 PPT 逻辑生成的 HTML slide 模板。

核心目标：
- 所有页面固定为 16:9 比例
- 每一页对应一个独立 slide
- 字体、字号、颜色、留白、logo、图片样式统一
- 所有图片资源默认内嵌为 base64 / data URI，便于单文件交付、预览、截图、右键另存与后续导出
- 整体气质偏公司报告，不做花哨网页感

## 固定规格

- 画布：1600 × 900 px
- 每页结构：header / main / footer
- 默认每页带 logo
- logo 固定右上角
- logo 高度：40–44 px
- 页面安全区：左右 80 px，上 64 px，下 56 px
- 封面页与封底页属于强制母版：默认必须沿用已确认模板的版式结构、logo 位置关系与信息层级，不自行重构
- 目录页与正文页允许根据用户输入自定义；若用户未给出明确自定义要求，则回落到模板预设版式

## 字体与色彩

- 中文字体：思源黑体（Source Han Sans SC / Noto Sans SC）
- 英文字体：Outfit
- 大英文标题：Outfit Bold
- 品牌红：`#CE3C27`
- 中性灰：`#626366`
- 深色文字：`#212121`

延展原则：
- 用色克制
- 红色主要用于点、线、标签、数字
- 不做蓝紫科技感
- 不做大面积高饱和渐变背景

## Slide 类型

当前固定支持 11 类：
- Cover Slide
- Agenda Slide
- Section Divider Slide
- Text-Image Slide
- Full-Image Slide
- Image Grid Slide
- Insight Slide
- Data / Highlight Slide
- Chart / Table Demo Slide
- Summary / Closing Slide
- Thank You Slide

## MVP

第一版至少支持：
- cover
- agenda
- text-image
- insight
- chart-table
- summary
- thank-you

其中：
- `chart-table` 承接条形图、折线图、扇形图、表格的标准排版
- `thank-you` 固定作为末页自动补齐

## Demo 联动规则

- 只要 skill 的版式、slide 类型、logo 尺寸、图表样式发生变化，都要同步更新 demo
- demo 不是附属参考图，而是 skill 当前输出能力的可视化样张
- 每次改 skill，至少回看一次 demo，确认新增规则在 16:9 翻页结构里成立

## 质检清单

结构检查：
- 每页都是独立 slide
- 维持 16:9 尺寸
- 包含 logo、header、footer 基础结构
- 包含固定的 thank-you 末页
- 若包含图表页，覆盖条形图 / 折线图 / 扇形图 / 表格四类示意

视觉检查：
- 字号层级稳定
- 正文信息层在小屏下仍可读，非装饰性正文建议不低于约 13–15 px 等效尺寸
- 与字号同步抬升关键行高、行间距、模块内 gap，避免只放大字不放大节奏
- chart / table / framework slide 默认使用更激进的图表字号规格，不沿用普通正文页的保守微字
- 柱图段内数字、单位 lockup、坐标字、矩阵说明、表头和关键数值在缩小观看时仍需可读
- 页内不过密
- 图片圆角、阴影、边距统一
- 一页只保留一个视觉重点

素材检查：
- 所有 logo / 图片 / 插图均为 base64 data URI 内嵌
- 不允许依赖相对路径图片文件或外部 URL
- logo 显示正常
- 用户只保存单个 HTML 文件时，离线打开仍能完整显示

## 当前演示文件

当前同步样张：
- `assets/alpha-company-report-demo.html`（英文版）
- `assets/alpha-company-report-demo-cn.html`（中文版）

用法：
- 浏览器直接打开预览
- 用于检视 cover / agenda / text-image / chart-table / summary / thank-you 的视觉状态
- 改 skill 时同步回看
