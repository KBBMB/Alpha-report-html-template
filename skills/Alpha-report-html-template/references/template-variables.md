# HTML 公司报告模板变量规则

> 这份文件面向 skill 实现层，不面向最终用户展示。

## 基本原则

- 最终渲染结果中，不显示 `{{...}}`、`[[...]]` 或其他占位符语法。
- 当用户没有提供某个字段时，自动生成自然、可展示的默认文案。
- 当用户提供字段时，用用户内容覆盖默认值。
- 封面与封底的小字属于可替换信息层，不写死为唯一固定文案。

## Cover 字段

### `cover_eyebrow`
- 用途：封面左上角小标题
- 默认：按语言模式生成，例如 `内部经营汇报` / `Internal strategy review`

### `cover_title`
- 用途：封面主标题
- 默认：根据用户主题自动整理成一句完整、结论式标题

### `cover_subtitle_or_audience`
- 用途：封面标题下的小字，可写汇报对象、项目说明、部门名
- 默认：
  - 中文：`{company_name} 内部管理汇报`
  - 英文：`Prepared for the {company_name} internal management review`

### `cover_date`
- 用途：封面日期
- 默认：按当前日期和语言模式自动格式化

### `cover_footer_note`
- 用途：封面左下角小字
- 默认：基于主题生成简短说明，例如：
  - 中文：`内部经营复盘与增长规划｜虚拟内容示例`
  - 英文：`Loyalty and growth strategy | virtual demo`

## Closing 字段

### `closing_eyebrow`
- 用途：封底 slogan 上方小字
- 默认：公司名

### `closing_slogan`
- 用途：封底主标语
- 默认：如果用户提供固定 slogan，则使用固定 slogan；当前样张默认 `Create better lives`

### `closing_footer_left`
- 用途：封底左下角小字
- 默认：公司名

### `closing_footer_right`
- 用途：封底右下角小字
- 默认：
  - 中文：`内部汇报模板中文版示例`
  - 英文：`Internal reporting template demo`

## 实现方式

- 在 HTML 中保留真实默认文案节点，并使用稳定 `id` 标记。
- 先构造 defaults，再合并 user inputs，最后回填到 HTML 节点。
- 不把变量名直接输出到用户成品。
- 封面页与封底页只替换允许替换的字段内容，不改母版结构。
- 目录页与正文页若收到用户自定义要求，则按要求生成；若未收到，则沿用模板预设。

## 小屏可读性策略

- 装饰性微字（如页脚 source / note、页码、辅助标签）可以保持更小字号。
- 正文信息层、目录条目、摘要解释、图表标签、表格正文、框架说明等，不要压到难读的小字号。
- 模板迭代时，优先统一抬升正文最小字号与对应 line-height / gap，而不是只局部放大某一页。
- 图表、表格、框架页视为单独的可读性层级：柱内百分比、单位说明、坐标字、矩阵块说明、表头、关键数值默认就要比普通正文页更大。

## 中文 HTML 字体策略

- 中文 HTML 交付优先使用：`Source Han Sans SC` / `Noto Sans SC`
- 次级回退：`Microsoft YaHei` / `PingFang SC`
- 避免对中文大标题使用过强负字距。
- 避免让整页通过容易造成断笔画的缩放路径渲染。

## 单文件交付要求

- 所有 logo / 图片 / 插图都必须内嵌为 base64 data URI。
- 用户只保存单个 HTML 文件时，离线打开仍需完整显示。
