---
title: 快速开始
order: 2
group:
  path: /
nav:
  title: 文档
  path: /docs
---

## ProComponents

ProComponents 是基于 Ant Design 而开发的模板组件，提供了更高级别的抽象支持，开箱即用。可以显著的提升制作 CRUD 页面的效率，更加专注于页面。

- [X6-React](/components/x6-react) 提供卡片切分以及栅格布局能力
- [ProSkeleton](/components/skeleton) 页面级别的骨架屏

在使用之前可以查看一下典型的 Demo 来判断组件是否适合你们的业务。ProComponents 专注于中后台的 CRUD, 预设了相当多的样式和行为。这些行为和样式更改起来会比较困难，如果你的业务需要丰富的自定义建议直接使用 Ant Design。

## 安装

当前 ProComponents 每一个组件都是一个独立的包，你需要在你的项目中安装对应的 npm 包并使用。

```shell
$ npm i @ant-design/pro-table --save
```

我们所有的包都使用 less 来进行样式管理，方便进行主题的自定义。如果你没有 less-loader 可以尝试从 `dist` 中导入 css。

```tsx | pure
import '@ant-design/pro-form/dist/form.css';
import '@ant-design/pro-table/dist/table.css';
import '@ant-design/pro-layout/dist/layout.css';
```

建议还是使用 less，可以方便进行主题自定义，也可以做到按需加载。
