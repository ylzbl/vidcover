# VidCover — 视频封面生成器

> 给视频做一张能打的封面图，3 分钟出图，纯浏览器完成。

[![GitHub](https://img.shields.io/badge/owner-ylzbl-blue)](https://github.com/ylzbl)
[![Pure HTML](https://img.shields.io/badge/pure-HTML%2FCSS%2FJS-orange)]()
[![Fonts](https://img.shields.io/badge/fonts-Alibaba%20PuHuiTi-red)]()

---

## 这是什么

VidCover 是一个**纯前端的视频封面生成工具**。上传一张截图或背景图，添加标题、副标题、Logo、装饰元素，调整排版后一键导出为高分辨率 PNG / JPG，用作 B 站、YouTube、视频号、小红书等平台的视频封面。

设计目标：

- 不开 Photoshop，浏览器里就能完成 80% 的封面需求
- 内置符合国内视频平台审美的字体和排版预设
- 支持横版（16:9）和竖版（9:16）一键切换
- 输出尺寸可调，满足不同平台规格

## 功能特性

### 排版
- 内置 **Alibaba PuHuiTi** 字体（Regular / Medium / Bold / Light 四种字重），本地化加载
- 主标题、副标题、正文三层结构
- 文字阴影、描边、渐变填充
- 多种对齐方式（左 / 中 / 右）
- 行高、字间距可调

### 视觉元素
- 背景图上传（支持拖拽）
- 蒙层颜色和透明度调整（保证文字可读性）
- Logo 添加（支持透明 PNG）
- 装饰元素（标签、序号、引导箭头）
- 渐变背景（无图时使用）

### 模板
- 内置多套封面模板（科技感、生活流、知识科普、Vlog 等）
- 模板支持参数化（颜色、字体、布局可调）
- 模板可保存为 JSON 自定义复用

### 导出
- 一键导出 PNG（透明背景可选）
- 导出 JPG（体积更小，适合社交平台）
- 多种分辨率预设：
  - B 站：1146 × 717
  - YouTube：1280 × 720
  - 视频号：750 × 1000（竖版）
  - 小红书：1080 × 1440
  - 自定义尺寸

## 使用方法

### 快速开始
1. 双击 `index.html` 在浏览器中打开
2. 上传背景图（或选择纯色 / 渐变背景）
3. 选择模板或从空白开始
4. 编辑标题、副标题
5. 调整字体、颜色、位置
6. 可选：添加 Logo、装饰
7. 点击「导出」选择格式和尺寸

### 部署
- **本地使用**：直接双击 `index.html`
- **GitHub Pages**：推送到仓库后启用 Pages
- **Cloudflare Pages**：直接连接 GitHub 仓库即可部署

## 文件结构

```
vidcover/
├── index.html             # 单文件应用（HTML + CSS + JS 全部内联，约 350KB）
├── AliPuHui-Regular.woff2 # 阿里巴巴普惠体 Regular
├── AliPuHui-Medium.woff2  # 阿里巴巴普惠体 Medium
├── AliPuHui-Bold.woff2    # 阿里巴巴普惠体 Bold
├── AliPuHui-Light.woff2   # 阿里巴巴普惠体 Light
├── logo_color.svg         # 彩色 Logo
├── logo_line_black.svg    # 黑色线稿 Logo
├── logo_text.svg          # 文字 Logo
├── search.jpg             # 搜索图标素材
└── README.md              # 本文件
```

## 技术实现

- **渲染**：纯 CSS + Canvas，导出时用 Canvas 重绘保证清晰度
- **字体**：本地 woff2 优先，缺失时回退到 jsDelivr CDN（`cdn.jsdelivr.net/gh/IlysvlVEizbr/via-font@0.3/AliPuHui.woff2`）
- **导出**：Canvas `toBlob()` + `download` 属性
- **零依赖**：不引入任何第三方 JS 库

## 注意事项

1. 首次加载字体（约 5MB）需要 1-2 秒，建议部署到 CDN
2. 导出大尺寸封面（>4K）时可能卡顿，建议先关闭其他浏览器标签
3. Logo 透明度需要在导出前设置好，导出后无法二次调整
4. 部分中文字符在 Light 字重下显示不清，建议正文用 Regular 及以上字重

## Roadmap

- [ ] 更多模板（节日、促销、教程系列）
- [ ] 支持视频帧抓取（直接从视频文件截取封面）
- [ ] AI 智能抠图（去除背景人物）
- [ ] 多封面批量生成（系列视频统一风格）
- [ ] 模板市场（用户分享 / 下载模板）
- [ ] 导出为 PSD（保留图层）

## License

版权所有 © 2026 娱乐资本论 / 小娱科技（北京）有限公司。保留所有权利（All Rights Reserved）。

本仓库内容（包括但不限于源代码、文档、设计、Logo、配置）的著作权完整归属版权所有者。
在法律允许的最大范围内，版权所有者就本作品保留全部权利。

未经版权所有者书面许可，严禁任何形式的商业使用、修改、再分发、网络传播或集成到
第三方产品中。本仓库的公开展示不构成对上述权利的默示许可。

第三方字体（阿里巴巴普惠体）的著作权归原作者所有，应遵循对应的字体授权条款，
本 LICENSE 不变更或扩展第三方字体的授权范围。仓库中的 Logo / 素材版权归
版权所有者所有，未经授权不得在任何场景下使用。

详细条款见仓库根目录 [LICENSE](./LICENSE) 文件。如需获取超出 LICENSE 范围的授权
（包括商业使用、内部部署、定制开发等），请联系：https://ylzbl.com/
