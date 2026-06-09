# zoehis-switch 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

`zoehis-switch` 是一个开关组件，支持 v-model 双向绑定、禁用状态、自定义开关文本（开/关）、自定义开关颜色、自定义开关值等功能。

## 基础用法

```vue
<!-- 基础开关 -->
<zoehis-switch v-model="value"></zoehis-switch>

<!-- 带文字说明 -->
<zoehis-switch v-model="value" ontext="开启" offtext="关闭"></zoehis-switch>

<!-- 自定义颜色 -->
<zoehis-switch v-model="value" oncolor="#13ce66" offcolor="#ff4949"></zoehis-switch>

<!-- 自定义开关值 -->
<zoehis-switch v-model="value" :onvalue="1" :offvalue="0"></zoehis-switch>

<!-- 禁用状态 -->
<zoehis-switch v-model="value" disabled></zoehis-switch>

<!-- 自定义宽度 -->
<zoehis-switch v-model="value" :width="80"></zoehis-switch>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| value | Boolean / String / Number | false | 绑定值（v-model） |
| disabled | Boolean | false | 是否禁用 |
| width | Number | 0 | 开关宽度，0 表示自动（有文字 58px，无文字 46px） |
| ontext | String | '' | 开启时显示的文字 |
| offtext | String | '' | 关闭时显示的文字 |
| oncolor | String | '' | 开启时的背景颜色 |
| offcolor | String | '' | 关闭时的背景颜色 |
| onvalue | Boolean / String / Number | true | 开启时对应的值 |
| offvalue | Boolean / String / Number | false | 关闭时对应的值 |
| name | String | '' | 原生 input 的 name 属性 |

## 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| input | (value) | 开关状态改变时触发（v-model） |
| change | (value) | 开关状态改变时触发 |

## 方法（Methods）

| 方法名 | 参数 | 说明 |
|--------|------|------|
| setBackgroundColor | — | 手动设置开关背景颜色 |

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 开关后面的附加内容 |
