# zoehis-multiple-select 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

`zoehis-multiple-select` 是一个多选下拉选择器组件，支持多选标签展示、搜索过滤、键盘导航、全选功能、自定义选项渲染、换行显示、滚动加载等多种功能。选中的选项以标签形式展示在输入框中，支持 Delete/Backspace 键删除。

## 基础用法

```vue
<!-- 基础多选 -->
<zoehis-multiple-select v-model="selectedList" :selectdata="options" itemcode="id" itemtext="text"></zoehis-multiple-select>

<!-- 可搜索 -->
<zoehis-multiple-select v-model="selectedList" :selectdata="options" filterable></zoehis-multiple-select>

<!-- 禁用状态 -->
<zoehis-multiple-select v-model="selectedList" :selectdata="options" disabled></zoehis-multiple-select>

<!-- 全选按钮 -->
<zoehis-multiple-select v-model="selectedList" :selectdata="options" :show-all-bt="true"></zoehis-multiple-select>

<!-- 默认显示全部 -->
<zoehis-multiple-select v-model="selectedList" :selectdata="options" :show-all="true"></zoehis-multiple-select>

<!-- 换行显示 -->
<zoehis-multiple-select v-model="selectedList" :selectdata="options" :is-wrap="true"></zoehis-multiple-select>

<!-- 自定义分隔符 -->
<zoehis-multiple-select v-model="selectedList" :selectdata="options" delimiter=","></zoehis-multiple-select>

<!-- 矩形边框样式 -->
<zoehis-multiple-select v-model="selectedList" :selectdata="options" ui-type="rectangle"></zoehis-multiple-select>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| value | Array | — | 绑定值（v-model，必填），数组格式 |
| selectdata | Array | [] | 下拉选项数据源 |
| itemcode | String | 'id' | 选项的唯一标识字段名 |
| itemtext | String | 'text' | 选项的显示文本字段名 |
| itemkey | String / Number | — | 选项的 key 字段名 |
| width | Number / String | 165 | 组件宽度 |
| placeholder | String | '' | 占位提示文本 |
| disabled | Boolean | false | 是否禁用 |
| clearable | Boolean | true | 是否支持清空 |
| filterable | — | — | 通过 filterMethod 实现搜索 |
| filterMethod | Function | — | 自定义模糊查询回调 |
| filterRowData | Function | — | 自定义过滤行数据 |
| filterField | Array | — | 过滤字段列表，默认 [itemtext, itemcode, 'spellCode', 'wbzxCode'] |
| delayTime | String / Number | 200 | 模糊查询延时时间（ms） |
| defaultfirst | Boolean | true | 是否默认选中第一项 |
| noMatchText | String | — | 无匹配数据时的提示文本 |
| beforeSelect | Function | — | 选中前事件 |
| renderItem | Function | — | 自定义选项渲染函数 |
| dropdownWidth | Number / String | — | 下拉框宽度 |
| dropdownMaxWidth | Number / String | '500px' | 下拉框最大宽度 |
| maxHeight | Number / String | — | 下拉列表最大高度 |
| delimiter | String | ';' | 选项标签间的分隔符 |
| align | String | 'left' | 弹窗对齐方式：left、center、right |
| uiType | String | '' | UI 样式：默认（下划线）、rectangle（矩形边框） |
| imeMode | String | 'auto' | 原生 ime-mode 属性 |
| preventOverId | String | '' | 防止被遮挡的容器 id |
| firstFocQuery | Boolean | false | 首次聚焦时是否聚焦到搜索框 |
| showAll | Boolean | false | 是否默认显示全部选项 |
| renderShowAll | Object | — | 自定义"全部"选项数据 |
| showAllBt | Boolean | false | 是否显示全选按钮 |
| isWrap | Boolean | false | 是否换行显示标签 |
| closeRz | Boolean | true | 内部临时使用，不建议使用 |

## 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| input | (value) | 选中值改变时触发（v-model） |
| change | (selected) | 选中值改变时触发 |
| select-change | (arr, curSelect, status) | 选项选中状态改变时触发 |
| clear | — | 清空时触发 |
| focus | — | 获取焦点时触发 |
| blur | — | 失去焦点时触发 |
| visible-change | (visible) | 下拉框显示/隐藏状态改变时触发 |
| scroll-to-bottom | (query) | 滚动到底部时触发 |
| scroll-to-top | (query) | 滚动到顶部时触发 |
| scroll-after | (query) | 滚动后触发 |
| searchClear | (e) | 搜索栏清空时触发 |
| drop-keydown | (event) | 下拉框键盘按下时触发 |
| drop-keyup | (event) | 下拉框键盘弹起时触发 |

## 方法（Methods）

| 方法名 | 参数 | 说明 |
|--------|------|------|
| focus | — | 手动聚焦到组件 |
| hide | — | 隐藏下拉框 |
| clearEvn | — | 清空所有选中项 |
| setSelectVal | (val) | 设置弹窗的选中值 |
| focusQuery | — | 聚焦到搜索框 |

## 插槽（Slots）

该组件无显式插槽定义，选项内容通过 `renderItem` 属性自定义。
