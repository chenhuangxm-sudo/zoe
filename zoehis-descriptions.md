# zoehis-descriptions / zoehis-descriptions-item 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

描述列表组件，以表格形式展示信息。`zoehis-descriptions` 为容器组件，`zoehis-descriptions-item` 为列表项组件。支持自定义列数、标签/内容字体加粗、冒号显示、多种尺寸、自定义样式等。

## 基础用法

```vue
<zoehis-descriptions title="用户信息" :column="3" size="default">
  <zoehis-descriptions-item label="姓名">张三</zoehis-descriptions-item>
  <zoehis-descriptions-item label="年龄">28</zoehis-descriptions-item>
  <zoehis-descriptions-item label="手机号">138****8888</zoehis-descriptions-item>
  <zoehis-descriptions-item label="邮箱">zhangsan@example.com</zoehis-descriptions-item>
  <zoehis-descriptions-item label="地址">北京市朝阳区</zoehis-descriptions-item>
</zoehis-descriptions>
```

---

## zoehis-descriptions 描述列表

### 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| title | String | '' | 描述列表标题 |
| column | Number | 3 | 一行显示的 Descriptions Item 数量 |
| labelBold | Boolean | false | 标签字体是否加粗 |
| textBold | Boolean | false | 内容字体是否加粗 |
| size | String | 'default' | 列表尺寸：default / small / mini |
| colon | Boolean | true | 是否显示冒号 |
| paddingBottom | Number/String | '' | 列表项的 padding-bottom |

### 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | zoehis-descriptions-item 列表项 |

---

## zoehis-descriptions-item 描述列表项

### 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| label | String | '' | 标签文本 |
| labelClassName | String | '' | 自定义标签类名 |
| contentClassName | String | '' | 自定义内容类名 |
| labelStyle | Object | {} | 自定义标签样式 |
| contentStyle | Object | {} | 自定义内容样式 |

### 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 列表项内容 |
