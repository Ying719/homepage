# 个人主页 · homepage

在线预览：**https://ying719.github.io**

一个用纯 HTML/CSS/JS 手写的单文件个人主页，没有任何框架和构建工具——打开 `index.html` 就能看，改完保存刷新即可生效。

## 这里有什么

| 板块 | 内容 |
|------|------|
| 首屏 | 姓名、专业方向、当前在跑的三条线（就业准备 / 工作室项目 / 导师课题组） |
| 01 现在在做的事 | 分团校学生工作、KingCola-ICG 工作室团队项目、张世文老师课题组 |
| 02 技能栈 | 编程语言、人工智能（机器学习 → 深度学习 → 大模型应用）、计算机基础、工具与环境 |
| 03 项目作品 | 独立完成的 AI 项目，**已开源的项目可直接点卡片跳转源码仓库** |
| 04 联系方式 | 邮箱、手机 |

## 关联的开源项目

主页上「项目作品」栏目的卡片可直接点击进入对应仓库：

- [MNIST 手写数字分类（ANN vs CNN 对照实验）](https://gitee.com/yiiiii_1_0/mnist-classification-cnn) — 测试准确率 99.20%
- [线性回归：从零走通 PyTorch 训练闭环](https://gitee.com/yiiiii_1_0/linear-regression-pytorch) — SGD / Adam 优化器对比

## 技术说明

- **单文件架构**：全部 HTML、CSS、JS 内联在 `index.html` 中，图片以 base64 内嵌，无外部依赖（除 Google Fonts），因此可以直接托管在任意静态服务上
- **内容与代码分离**：所有展示内容集中在文件内的 `<script type="text/x-config" id="site-config">` 配置块里，改文字不需要碰渲染逻辑。渲染器支持 `text` / `cards` / `tags` / `timeline` / `contact` 五种板块类型
- **在线编辑**：本地以 `file://` 打开或网址带 `#edit` 时，页面会显示「编辑内容」入口，可在浏览器里直接改内容并实时预览
- **响应式**：移动端自动折叠为单列布局

## 怎么改内容

1. 用编辑器打开 `index.html`
2. 找到 `<script type="text/x-config" id="site-config">` 配置块
3. 修改里面的文字（比如 `motto` 是页脚座右铭，`projects` 是项目卡片列表）
4. 保存 → 刷新浏览器即可看到效果

想新增一个项目卡片，复制 `items` 数组中相邻的一个 `{ ... }` 块，改内容并在末尾加逗号。带 `href` 字段的卡片会自动变成可点击的链接（新窗口打开）。

## 部署方式

托管在 **GitHub Pages** 上（Gitee Pages 服务已停止运营，故不用 Gitee 部署）：

- 仓库名：`Ying719.github.io`（用户主站仓库名必须与用户名一致）
- 部署分支：`master`，目录 `/`（根目录）

每次 `git push` 到 GitHub 后约 1 分钟自动更新，无需手动操作。Gitee 仓库仅作为国内镜像备份。
