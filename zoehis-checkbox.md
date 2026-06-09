# zoehis-checkbox 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

`zoehis-checkbox` 是一个复选框组件，支持 v-model 双向绑定、禁用状态、自定义选中值（trueflag/falseflag）、选中前事件拦截等功能。配合 `zoehis-checkbox-group` 复选框组组件可实现多选分组。

## 基础用法

```vue
<!-- 基础复选框 -->
<zoehis-checkbox v-model="checked">选项A</zoehis-checkbox>

<!-- 禁用状态 -->
<zoehis-checkbox v-model="checked" disabled>禁用选项</zoehis-checkbox>

<!-- 自定义选中值 -->
<zoehis-checkbox v-model="value" :trueflag="1" :falseflag="0">启用</zoehis-checkbox>

<!-- 选中前事件拦截 -->
<zoehis-checkbox v-model="checked" :before-select="beforeSelectFn">需确认</zoehis-checkbox>

<!-- 复选框组 -->
<zoehis-checkbox-group v-model="checkedList">
  <zoehis-checkbox label="A">选项A</zoehis-checkbox>
  <zoehis-checkbox label="B">选项B</zoehis-checkbox>
</zoehis-checkbox-group>
```

## 属性（Props）

### ZoehisCheckbox

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| value | — | — | 绑定值（v-model） |
| label | — | — | 复选框的标签值，在组中作为选中标识 |
| disabled | Boolean | false | 是否禁用 |
| checked | Boolean | false | 初始是否选中 |
| name | String | — | 原生 input 的 name 属性 |
| trueflag | String / Boolean / Number | true | 选中时对应的值 |
| falseflag | String / Boolean / Number | false | 未选中时对应的值 |
| beforeSelect | Function | — | 选中前事件，返回 false 阻止选中，第二个参数为 item |
| item | Object / String / Boolean / Number | — | 作为 beforeSelect 的第二个参数传递 |
| strictflag | Boolean | false | trueflag 是否需要全等比较，默认 false（宽松比较） |
| validateEvent | Boolean | true | 内部使用，是否触发表单校验事件 |

### ZoehisCheckboxGroup

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| value | — | — | 绑定值（v-model），数组类型 |
| validateEvent | Boolean | true | 内部使用，是否触发表单校验事件 |

## 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| input | (value) | 值改变时触发（v-model） |
| inputnative | (value) | 原生 input 事件 |
| change | (value) | 值改变时触发 |
| click | ([selfModel, event]) | 点击复选框时触发 |
| enter | (evt) | 键盘回车时触发 |
| focus | — | 获取焦点时触发 |
| blur | (event) | 失去焦点时触发 |

## 方法（Methods）

| 方法名 | 参数 | 说明 |
|--------|------|------|
| focus | — | 手动聚焦到复选框 |
| getDisabled | — | 获取是否禁用状态，返回 Boolean |

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 复选框标签文本内容，未提供时显示 label 值 |
