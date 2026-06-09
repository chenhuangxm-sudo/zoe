# zoehis-tag-group 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

标签组组件，用于管理一组标签。支持新增标签（输入框/按钮/浮窗三种方式）、标签关闭、自定义主题颜色、Popover 浮窗等功能。配合 `zoehis-tag` 子组件使用。

## 基础用法

```vue
<zoehis-tag-group
  btnType="addInput"
  :closable="true"
  @inputConfirm="handleInputConfirm"
  @closeClick="handleClose"
>
  <zoehis-tag
    v-for="tag in tags"
    :key="tag.key"
    :code="tag.key"
    :closable="true"
  >
    {{ tag.name }}
  </zoehis-tag>
</zoehis-tag-group>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| btnType | String | 'addInput' | 按钮类型：addInput（添加输入框）/ addBtn（添加按钮）/ popover（浮窗）/ none（不要） |
| popoverCustom | Object | {} | 自定义 Popover 配置，支持 width/height/trigger/disabled/offsetX/offsetY/placement/visibleFlag |
| closable | Boolean | false | 是否可关闭 |
| showAddButton | Boolean | true | 是否展示新增按钮 |
| type | String | 'form' | 功能类型 |
| addInputTrigger | String/Number | '1' | 新增输入框触发类型：1（失焦和回车）/ 2（仅失焦）/ 3（仅回车） |
| theme | String | 'default' | 样式主题：default / other |
| color | String | '' | 自定义字体颜色 |
| backgroundColor | String | '' | 自定义背景颜色 |

## 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| tagClick | (code, event, data) | 点击标签时触发 |
| closeClick | (code, event, data) | 点击删除图标时触发 |
| inputConfirm | (inputValue) | 新增输入框确认时触发 |
| addBtnClick | - | 点击新增按钮时触发 |
| show | - | Popover 弹窗显示时触发 |
| hide | - | Popover 弹窗隐藏时触发 |
| focus | (event) | 聚焦到新增按钮或输入框时触发 |
| blur | (event) | 新增按钮失焦时触发 |

## 方法（Methods）

| 方法名 | 参数 | 说明 |
|--------|------|------|
| focus | (event) | 聚焦到新增按钮或输入框 |
| getSlotMaps | - | 获取标签组下默认 slot 的相关信息 |

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 标签列表（zoehis-tag） |
| operate | 操作区域（新增按钮/输入框/Popover），不传则使用默认 |
| popover | Popover 浮窗内容（btnType='popover' 时有效） |
