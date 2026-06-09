# zoehis-radio 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

`zoehis-radio` 是一个单选框组件，支持 v-model 双向绑定、禁用状态、聚焦样式、可点击清空（再次点击取消选中）等功能。配合 `zoehis-radio-group` 单选框组组件可实现单选分组。

## 基础用法

```vue
<!-- 基础单选框 -->
<zoehis-radio v-model="value" label="A">选项A</zoehis-radio>
<zoehis-radio v-model="value" label="B">选项B</zoehis-radio>

<!-- 禁用状态 -->
<zoehis-radio v-model="value" label="A" disabled>禁用选项</zoehis-radio>

<!-- 可点击清空 -->
<zoehis-radio v-model="value" label="A" clearable>可取消选中</zoehis-radio>

<!-- 单选框组 -->
<zoehis-radio-group v-model="value">
  <zoehis-radio label="1">选项一</zoehis-radio>
  <zoehis-radio label="2">选项二</zoehis-radio>
</zoehis-radio-group>

<!-- 单选框组 - 带点击前事件 -->
<zoehis-radio-group v-model="value" :before-click="beforeClickFn">
  <zoehis-radio label="1">需确认</zoehis-radio>
</zoehis-radio-group>
```

## 属性（Props）

### ZoehisRadio

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| value | — | — | 绑定值（v-model） |
| label | — | — | 单选框的标签值，选中时 model 等于该值 |
| disabled | Boolean | false | 是否禁用 |
| name | String | — | 原生 input 的 name 属性 |
| tabindex | — | — | 原生 tabindex 属性 |
| tabNum | — | — | 保留字段 |
| isShowFocus | Boolean | false | 是否显示聚焦样式 |
| clearable | Boolean | false | 是否允许点击清空（已选中时再次点击取消选中） |

### ZoehisRadioGroup

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| value | — | — | 绑定值（v-model） |
| disabled | Boolean | false | 是否禁用整个组 |
| isShowFocus | Boolean | false | 是否显示聚焦样式 |
| beforeClick | Function | — | 点击前事件，返回 true 继续选中，否则阻止 |
| clearable | Boolean | false | 是否允许点击清空 |
| validateEvent | Boolean | true | 内部使用，是否触发表单校验事件 |

## 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| input | (value) | 值改变时触发（v-model） |
| inputnative | (value) | 原生 input 事件 |
| click | (label, model) | 点击单选框时触发 |
| focus | (label) | 获取焦点时触发 |
| blur | (label) | 失去焦点时触发 |

## 方法（Methods）

| 方法名 | 参数 | 说明 |
|--------|------|------|
| focus | — | 手动聚焦到单选框 |

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 单选框标签文本内容 |
