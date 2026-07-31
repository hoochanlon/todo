# Todo

一个纯静态、免登录、可离线使用的待办事项网页应用。

项目基于原版 Uiineed Todo List 调整，当前版本保留轻量静态部署方式，并补充了作者信息、回收站、彻底删除、一键清空回收站、数据导入导出和 GitHub Pages 自动部署。

## 在线与入口

本项目没有构建步骤，直接打开 HTML 文件即可使用：

- 英文版：`index.html`
- 中文版：`index-zh.html`

本地预览方式：

```bash
open index.html
open index-zh.html
```

也可以启动一个本地静态服务：

```bash
python3 -m http.server 8080
```

然后访问：

- `http://localhost:8080/index.html`
- `http://localhost:8080/index-zh.html`

## 功能

- 新增、编辑、删除待办事项
- 标记单条待办为完成或未完成
- 一键标记全部为完成
- 清除已完成待办
- 清除全部待办
- 回收站过滤视图
- 从回收站还原待办
- 从回收站彻底删除单条待办
- 一键清空回收站
- 拖拽排序待办列表，仅适用于 PC 端
- 双击编辑顶部标语
- 中文与英文页面切换
- 导出当前待办数据
- 导入 `.txt` 或 `.json` 数据，并追加到当前列表
- 使用浏览器 `localStorage` 保存数据
- 待办列表和回收站均支持刷新后保留

## 数据存储

所有数据都保存在浏览器本地，不需要账号，也不会上传到服务器。

当前使用的本地存储键：

| 数据 | localStorage key |
| --- | --- |
| 待办列表 | `uiineed-todos` |
| 回收站 | `uiineed-recycle-bin` |
| 页面语言 | `uiineed-todos-lang` |
| 顶部标语 | `uiineed-slogan` |

清理浏览器缓存或手动删除这些 `localStorage` 数据后，页面中的待办数据也会被清空。

## 项目结构

```text
.
├── index.html                  # 英文入口
├── index-zh.html               # 中文入口
├── LICENSE                     # MIT License
├── README.md                   # 项目说明
├── .github/workflows/
│   └── deploy.yml              # GitHub Pages 自动部署
└── public/
    ├── css/
    │   ├── normalize.css
    │   ├── style.css
    │   ├── style.min.css
    │   └── style.scss
    ├── img/
    │   ├── author-1.jpg
    │   ├── author-2.png
    │   ├── delete.svg
    │   ├── restore.svg
    │   ├── todo.svg
    │   └── social/
    └── js/
        └── vue.js
```

## 部署到 GitHub Pages

项目已包含 GitHub Actions 部署配置：

```text
.github/workflows/deploy.yml
```

使用方式：

1. 将代码推送到 GitHub 仓库。
2. 打开仓库的 `Settings`。
3. 进入 `Pages`。
4. 将 `Source` 设置为 `GitHub Actions`。
5. 推送到 `main` 或 `master` 后会自动部署。

常用提交命令：

```bash
git add .
git commit -m "docs: rewrite README"
git push
```

## 自定义作者与仓库链接

页面顶部和作者弹窗信息位于：

- `index.html`
- `index-zh.html`

当前页面包含两位作者信息：

| 名称 | 说明 | 链接 |
| --- | --- | --- |
| ricocc | 原作者 | `https://ricoui.com/?ref=todo` |
| hoochanlon | 开源贡献者 | `https://github.com/hoochanlon` |

顶部 GitHub 图标当前指向：

```text
https://github.com/hoochanlon/todo
```

如需修改仓库地址，分别更新 `index.html` 与 `index-zh.html` 中对应的 GitHub 链接。

## 导入与导出

页面支持导出当前待办数据，导出内容是 JSON 格式文本。

导入支持：

- `.txt`
- `.json`

导入行为是追加到当前列表，不会覆盖已有待办。

## 技术说明

这是一个传统静态网页项目，不依赖 Node.js 构建流程。

主要技术：

- HTML
- CSS / Sass
- Vue 2.x，本地文件位于 `public/js/vue.js`
- Browser `localStorage`
- GitHub Actions
- GitHub Pages

## 原项目来源

本项目基于 Uiineed Todo List 修改。

原作者：ricocc

当前维护：hoochanlon

## License

本项目使用 MIT License。详见 [LICENSE](./LICENSE)。
