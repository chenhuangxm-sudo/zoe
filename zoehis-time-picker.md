# zoehis-time-picker 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

`zoehis-time-picker` 是一个时间选择器组件，基于 `zoehis-input` 封装，支持时分秒选择、上下键调节、键盘输入、时间范围限制、自定义格式等功能。

## 基础用法

```vue
<template>
  <zoehis-time-picker
    v-model="timeValue"
    placeholder="选择时间"
    @change="handleChange"
  ></zoehis-time-picker>
</template>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| value | — | — | 绑定值，支持 v-model |
| defaultValue | — | — | 默认值（点击展开后默认选中的值） |
| format | String | — | 显示格式，如 `'HH:mm:ss'` |
| readonly | Boolean | false | 是否只读 |
| disabled | Boolean | false | 是否禁用 |
| clearable | Boolean | true | 是否可清空 |
| showclose | Boolean | true | 是否显示清空按钮 |
| align | String | 'left' | 弹出窗对齐方式：`left`、`center`、`right` |
| placeholder | String | — | 输入框占位文本（通过 input 组件传递） |
| popperClass | String | — | 弹出面板的自定义 class |
| pickerOptions | Object | — | 时间选择器独有参数，如 `{ selectableRange: '18:30:00 - 20:30:00' }` |
| rangeSeparator | String | ' - ' | 时间范围选择的分隔符 |
| tabInner | Boolean | false | Tab 键是否进行时分秒切换 |
| pickerWidth | Number/String | 133 | 时间弹出框宽度 |
| width | Number/String | 133 | 输入框宽度 |
| standardtype | Boolean | false | 是否返回标准时间格式 |
| icon | String | 'z_timeA_normal' | 输入框图标 |
| errorTip | String | '' | 错误提示内容 |
| showErrorTip | Boolean | false | 是否显示错误提示 |
| imeMode | String | 'disabled' | 输入法引擎模式 |
| minErrorWidth | String/Number | — | 错误提示最小宽度 |
| uiType | String | '' | UI 样式：`''`（默认下划线）、`'rectangle'`（矩形边框） |
| liveUpdate | Boolean | true | 是否实时更新 |
| validateEvent | Boolean | true | 是否触发表单验证 |
| enabledRange | Object | {} | 可选时间范围 |
| preventOverId | String | — | 防止重叠的元素 ID |

## 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| input | value | 输入值变化时触发 |
| change | value | 值改变时触发 |
| focus | component | 获取焦点时触发 |
| blur | component | 失去焦点时触发 |
| show | value | 弹出面板显示时触发 |
| hide | value | 弹出面板隐藏时触发 |
| inputnative | value | 原生输入事件触发 |
| click-now | — | 点击"当前"按钮时触发 |
| click-sure | — | 点击"确认"按钮时触发 |
| tab | (value, displayValue) | Tab 键离开时触发 |
| enter | (value, displayValue) | Enter 键按下时触发 |

## 插槽（Slots）

无插槽定义。

## 方法（Methods）

| 方法名 | 参数 | 说明 |
|--------|------|------|
| focus | — | 使输入框获取焦点 |
| getTime | (isFormat) | 获取当前时间值，可指定格式 |
| setTime | (value) | 设置时间控件的值 |
| hide | — | 隐藏时间弹出面板 |
