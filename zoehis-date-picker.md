# zoehis-date-picker 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

`zoehis-date-picker` 是一个日期选择器组件，支持单日期选择、日期范围选择、日期时间选择，可配置快捷键、自定义按钮、禁用日期、手动输入等功能。

## 基础用法

```vue
<template>
  <zoehis-date-picker
    v-model="dateValue"
    type="date"
    placeholder="选择日期"
    @change="handleChange"
  ></zoehis-date-picker>
</template>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| value | — | — | 绑定值，支持 v-model |
| type | String | 'date' | 选择器类型：`date`（单日期）、`daterange`（日期范围）、`datetime`（日期时间） |
| dateType | String | 'worldTime' | 返回给父组件 v-model 的类型 |
| placeholder | String | '选择日期' | 输入框占位文本 |
| disabled | Boolean | false | 是否禁用 |
| readonly | Boolean | false | 是否只读 |
| clearable | Boolean | true | 是否可清空 |
| width | String | — | 输入框宽度 |
| format | String | '' | 显示在输入框中的格式 |
| align | String | 'left' | 下拉面板对齐方式：`left`、`center`、`right` |
| icon | String | 'z_time_normal' | 输入框图标 |
| hasTime | Boolean | false | 单日期选择是否显示时分秒 |
| oneDateHasTime | Boolean | true | 单日期 emit 的时间是否包含时分秒 |
| rangeedit | Boolean | false | 日期范围是否支持手工输入 |
| originalVal | Boolean | false | 初始值保持原样不转换 |
| dateInitFlag | Boolean | true | 输入框为空时，日期组件默认选中今天 |
| disabledDateFun | Function | — | 禁用日期的函数 |
| endDateOver | Boolean | false | 设置结束日期时分秒为 23:59:59（仅 daterange 有效） |
| nowBtn | Boolean | false | 是否显示"当前"按钮 |
| nowBtnText | String | '当前' | "当前"按钮文本 |
| beforeClick | Function | — | 点击确认前回调，返回 false 阻止确认 |
| setGetDateType | String | '1' | 设置返回时间类型：`1` 国际时间，`2` 时间戳 |
| originDate | — | — | 原始日期值 |
| errorTip | String | '' | 错误提示内容 |
| showErrorTip | Boolean | false | 是否显示错误提示 |
| imeMode | String | 'disabled' | 输入法引擎模式 |
| preventOverId | String | '' | 防止重叠的元素 ID |
| onlyPanel | Boolean | false | 是否仅显示面板 |
| btnArr | Array | [] | 快捷按钮数组 |
| rangeBtn | Object | — | 范围选择快捷按钮配置 |
| dateBtn | Object | — | 单日期快捷按钮配置 |
| timeEnterFlag | Boolean | false | 时分秒组件按 Enter 是否触发确认 |
| initStartTime | Object | — | 初始化开始时间（datetime 有效） |
| initEndTime | Object | — | 初始化结束时间（datetime 有效） |
| minErrorWidth | String/Number | — | 错误提示最小宽度 |
| uiType | String | '' | UI 样式：`''`（默认下划线）、`'rectangle'`（矩形边框） |
| liveUpdate | Boolean | true | 是否实时更新 |
| correction | Number | 1 | 手工输入错误修正方式：1 修正为原值，2 修正为空值 |
| enabledRange | Object | {} | 可选时间范围 |

## 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| input | value | 输入值变化时触发 |
| change | value | 日期选择变化时触发 |
| focus | — | 输入框聚焦时触发 |
| show | — | 下拉面板显示时触发 |
| hide | — | 下拉面板隐藏时触发 |
| pickerBlur | — | 下拉面板失焦时触发 |
| click-now | — | 点击"当前"按钮时触发 |

## 插槽（Slots）

无插槽定义。

## 方法（Methods）

| 方法名 | 参数 | 说明 |
|--------|------|------|
| focus | — | 使输入框获取焦点 |
| changePanel | (isShow) | 显示/隐藏下拉面板 |
| clickClearDate | (isClear, isFirst) | 清空日期 |
| getPanelVirtualTime | — | 获取面板当前显示的时间 |
