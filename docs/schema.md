﻿---
title: 通用配置总览
order: 1
group:
  path: /
nav:
  title: 组件
  path: /components
---

# 通用配置

在 ProComponents 我们在组件使用了与 table 的相同的定义，同时扩展了部分字段。让其可以满足更多需求。

| 字段名称 | 类型 | 说明 |
| --- | --- | --- |
| `key` | `React.key` | 确定这个列的唯一值,一般用于 dataIndex 重复的情况 |
| `dataIndex` | `React.key` \| `React.key[]` | 与实体映射的 key，数组会被转化 `[a,b] => Entity.a.b` |
| `valueType` | `ProFieldValueType` | 数据的渲渲染方式，我们自带了一部分，你可以可以自定义 valueType |
| `title` | `ReactNode` \|`(props,type,dom)=> ReactNode` | 标题的内容，在 form 中是 label |
| `tooltip` | `string` | 会在 title 旁边展示一个 icon，鼠标浮动之后展示 |
| `valueEnum` | `(Entity)=> ValueEnum` \| `ValueEnum` | 支持 object 和 Map，Map 是支持其他基础类型作为 key |
| `fieldProps` | `(form,config)=>fieldProps`\| `fieldProps` | 传给渲染的组件的 props，自定义的时候也会传递 |
| `formItemProps` | `(form,config)=>formItemProps` \| `formItemProps` | 传递给 Form.Item 的配置 |
| `renderText` | `(text: any, record: Entity, index: number, action: ProCoreActionType) => any` | 修改的数据是会被 valueType 定义的渲染组件消费 |
| `render` | `(dom,entity,index, action, schema) => React.ReactNode` | 自定义只读模式的 dom,`render` 方法只管理的只读模式，编辑模式需要使用 `renderFormItem` |
| `renderFormItem` | `(schema,config,form) => React.ReactNode` | 自定义编辑模式,返回一个 ReactNode，会自动包裹 value 和 onChange |
| `request` | `(params,props) => Promise<{label,value}[]>` | 从远程请求网络数据，一般用于选择类组件 |
| `params` | `Record<string, any>` | 额外传递给 `request` 的参数，组件不做处理,但是变化会引起`request` 重新请求数据 |
| `hideInForm` | `boolean` | 在 Form 中隐藏 |
| `hideInTable` | `boolean` | 在 Table 中隐藏 |
| `hideInSearch` | `boolean` | 在 Table 的查询表单中隐藏 |
| `hideInDescriptions` | `boolean` | 在 descriptions 中隐藏 |

## valueType

valueType 是 ProComponents 的灵魂，ProComponents 会根据 valueType 来映射成不同的表单项。以下是支持的常见表单项：

| valueType       | 说明                         |
| --------------- | ---------------------------- |
| `password`      | 密码输入框                   |
| `money`         | 金额输入框                   |
| `textarea`      | 文本域                       |
| `date`          | 日期                         |
| `dateTime`      | 日期时间                     |
| `dateWeek`      | 周                           |
| `dateMonth`     | 月                           |
| `dateQuarter`   | 季度输入                     |
| `dateYear`      | 年份输入                     |
| `dateRange`     | 日期区间                     |
| `dateTimeRange` | 日期时间区间                 |
| `time`          | 时间                         |
| `timeRange`     | 时间区间                     |
| `text`          | 文本框                       |
| `select`        | 下拉框                       |
| `checkbox`      | 多选框                       |
| `rate`          | 星级组件                     |
| `radio`         | 单选框                       |
| `radioButton`   | 按钮单选框                   |
| `progress`      | 进度条                       |
| `percent`       | 百分比组件                   |
| `digit`         | 数字输入框                   |
| `second`        | 秒格式化                     |
| `avatar`        | 头像                         |
| `code`          | 代码框                       |
| `switch`        | 开关                         |
| `fromNow`       | 相对于当前时间               |
| `image`         | 图片                         |
| `jsonCode`      | 代码框，但是带了 json 格式化 |
| `color`         | 颜色选择器                   |

这里 demo 可以来了解一下各个 valueType 的展示效果。

### 传入 function

只有一个值并不能表现很多类型，`progress` 就是一个很好的例子。所以我们支持传入一个 function。你可以这样使用：

```tsx |pure
const columns = {
  title: '进度',
  key: 'progress',
  dataIndex: 'progress',
  valueType: (item: T) => ({
    type: 'progress',
    status: item.status !== 'error' ? 'active' : 'exception',
  }),
};
```

### 支持的返回值

#### progress

```js
return {
  type: 'progress',
  status: 'success' | 'exception' | 'normal' | 'active',
};
```

#### money

```js
return { type: 'money', locale: 'en-Us' };
```

#### percent

```js
return { type: 'percent', showSymbol: true | false, precision: 2 };
```

