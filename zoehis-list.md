# zoehis-list / zoehis-list-item 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

列表组件，支持普通列表和卡片列表两种模式。`zoehis-list` 为列表容器，`zoehis-list-item` 为列表项。支持网格布局、复选框多选、编辑模式、自定义图标、边框控制等功能。

## 基础用法

```vue
<zoehis-list :bordered="true" :showIcon="true">
  <zoehis-list-item
    v-for="item in listData"
    :key="item.key"
    :data="item"
    :title="item.title"
    itemcode="key"
    itemtitle="title"
  >
  </zoehis-list-item>
</zoehis-list>
```

---

## zoehis-list 列表

### 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| editable | Boolean | false | 是否可编辑 |
| grid | Boolean | false | 是否启用网格模式 |
| column | Number | 4 | 网格列数（grid=true 时生效） |
| icon | String | 'z_youjiantou_normal' | 右侧图标类名 |
| bordered | Boolean | true | 是否显示边框 |
| showIcon | Boolean | true | 是否显示右侧图标 |
| mode | String | 'sample' | 列表模式：sample / card |
| gutter | Number/String | - | 列表项间距 |
| size | String | 'default' | 尺寸：default / small |
| bgcolor | Boolean | false | 是否启用背景色 |
| gutterSide | Boolean | true | 网格模式下是否显示侧边间距 |
| editIcon | String | 'z_qingchu_normal' | 编辑图标类名 |
| checkbox | Boolean | false | 是否启用复选框 |
| editIconClassName | String | '' | 编辑图标样式类名 |

### 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| clickEditIcon | (code, event, data) | 点击编辑图标时触发 |
| clickItem | (code, event, data) | 点击列表项时触发 |
| clickIcon | (code, event, data) | 点击右侧图标时触发 |

### 方法（Methods）

| 方法名 | 参数 | 说明 |
|--------|------|------|
| getCkeckedList | - | 获取复选框已选择项列表 |
| toggleAllRowSelection | (flag) | 全选或清空选择 |
| toggleMultiRowSelection | (rows, selected) | 切换多行选中状态 |
| toggleRowSelection | (row, selected) | 切换某行选中状态 |

### 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | zoehis-list-item 列表项 |

---

## zoehis-list-item 列表项

### 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| title | String | '' | 列表项标题 |
| data | Object/Array | - | 列表项数据 |
| editIconClickEn | Function | null | 编辑图标点击函数 |
| code | String/Number | '' | 列表项标识 |
| editIcon | String | - | 自定义编辑图标类名 |
| editIconClassName | String | - | 自定义编辑图标样式类名 |
| itemcode | String | 'key' | 列表项 code 字段名 |
| itemtitle | String | 'title' | 列表项 title 字段名 |

### 方法（Methods）

| 方法名 | 参数 | 说明 |
|--------|------|------|
| remove | - | 从列表中移除当前项 |

### 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 列表项默认内容 |
| renderItem | 自定义渲染内容 |
| action | 右侧操作区域 |
| editIcon | 编辑状态图标 |
