# 个人主页 · homepage

> 在线访问：**https://ying719.github.io/homepage/**
>
> 一个用纯 HTML / CSS / JS 手写的单文件个人主页 —— 没有框架，没有构建工具，打开 `index.html` 就能看，改完保存刷新即生效。

<p align="center">
  <img src="https://img.shields.io/badge/HTML-单文件-E34F26?logo=html5&logoColor=white" alt="HTML">
  <img src="https://img.shields.io/badge/CSS-原生-1572B6?logo=css3&logoColor=white" alt="CSS">
  <img src="https://img.shields.io/badge/JS-原生-F7DF1E?logo=javascript&logoColor=black" alt="JS">
  <img src="https://img.shields.io/badge/依赖-零-4CAF50" alt="零依赖">
</p>

---

## 项目简介

这是我（马湘莹，湖南科技大学计算机科学与工程学院软件工程专业大二）的个人主页。做它的初衷很简单：**把简历上写的东西变成能点开看的实物**。

它的设计目标是三件事：

- **极简**：整个站点就是一个 `index.html`，双击就能在本地跑
- **内容与代码分离**：所有文案集中在文件顶部一个配置块里，改文字不用碰渲染逻辑
- **零依赖**：图片全部内嵌为 base64，除了 Google Fonts 没有外部请求

---

## 页面结构

| 板块 | 内容 |
|------|------|
| **首屏** | 姓名、专业方向，以及当前并行的四条线（就业准备 / 工作室竞赛项目 / 导师课题组 / 学生工作） |
| **01 现在在做的事** | 学院分团校学生工作、KingCola-ICG 工作室团队项目、张世文老师本科生课题组 |
| **02 技能栈** | 编程语言、人工智能（机器学习 → 深度学习 → 大模型应用）、计算机基础、工具与环境 |
| **03 项目作品** | 独立完成的 AI 项目，**已开源的卡片可直接点击跳转源码仓库** |
| **04 联系方式** | 邮箱、手机 |
| **页脚** | 座右铭 + 最近更新时间 |

---

## 关联的开源项目

主页「项目作品」栏目的卡片可直接点击进入对应仓库：

| 项目 | 说明 | 亮点 |
|------|------|------|
| [MNIST 手写数字分类](https://github.com/Ying719/mnist-classification) | ANN 与 CNN 双模型实现，从零走通完整训练流程 | 对照实验：准确率 97.73% → **99.20%**，错误率降低 65% |
| [线性回归 · PyTorch](https://github.com/Ying719/linear-regression-pytorch) | 从零走通 PyTorch 训练闭环（前向 → 损失 → 反向 → 更新） | SGD / Adam 优化器对比，拟合参数误差 < 1% |

两个项目在 Gitee 上均有国内镜像（[MNIST](https://gitee.com/yiiiii_1_0/mnist-classification-cnn) / [线性回归](https://gitee.com/yiiiii_1_0/linear-regression-pytorch)），访问更稳定。

---

## 技术实现

### 单文件架构

全部 HTML、CSS、JS（含渲染逻辑）内联在 `index.html` 中，图片以 base64 编码内嵌。整个站点**只有一个文件**，因此可以原样托管在任何静态服务上——GitHub Pages、Vercel、对象存储，甚至发微信里。

### 配置驱动的渲染器

所有展示内容集中在 `<script type="text/x-config" id="site-config">` 配置块里，由一套声明式渲染器负责生成 DOM。渲染器支持五种板块类型：

| 类型 | 用途 |
|------|------|
| `text` | 纯文本段落 |
| `cards` | 卡片网格（项目、经历） |
| `tags` | 标签云（技能栈） |
| `timeline` | 时间线（学生工作、学习路径） |
| `contact` | 联系方式列表 |

卡片支持可选的 `href` 字段，填了就会自动变成可点击链接，并带新窗口打开与悬停反馈。

### 页面内的在线编辑

本地以 `file://` 协议打开，或网址带上 `#edit` 时，页面右上角会出现「编辑内容」入口——可以在浏览器里直接改文案并实时预览效果。改完后点「复制全部」，把配置粘回文件即可持久化。**线上访客看不到这个入口。**

### 其他细节

- **响应式**：移动端自动折叠为单列布局
- **滚动动效**：基于 `IntersectionObserver` 实现元素进入视口的渐显，以及导航栏的高亮跟随
- **星空背景**：整页浅蓝星空 + 白色磨砂卡片（`backdrop-filter`），首屏右侧独立展示夜景图
- **更新日期自动计算**：页脚的「最近更新」默认显示打开页面当天的日期，无需手动维护

---

## 怎么改内容

1. 用任意编辑器打开 `index.html`
2. 找到 `<script type="text/x-config" id="site-config">` 配置块
3. 修改里面的文案（`motto` 是页脚座右铭，`projects` 是项目卡片列表，`meta.updated` 留空则自动显示当天日期）
4. 保存 → 刷新浏览器即可看到效果

**新增一个项目卡片**：复制 `items` 数组中相邻的一个 `{ ... }` 块，改内容，注意末尾加逗号。

**新增一个板块**：按五种类型之一的格式在 `sections` 数组中追加一项即可。

---

## 部署

托管在 **GitHub Pages**：

| 项 | 值 |
|----|-----|
| 仓库 | `Ying719/homepage` |
| 分支 | `master` |
| 目录 | `/`（根目录） |
| 访问地址 | **https://ying719.github.io/homepage/** |

推送到 GitHub 后约 1 分钟自动构建发布，**无需任何手动操作**。

Gitee 仓库 `yiiiii_1_0/homepage` 作为国内镜像同步保留（Gitee Pages 服务已于 2025 年停止运营，故不用其部署）。

---

## 许可

个人主页内容（文字、图片）版权归作者所有，请勿直接复制粘贴用于自己的主页；代码结构与实现方式欢迎参考。
