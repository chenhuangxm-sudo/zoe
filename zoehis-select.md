# zoehis-select 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

`zoehis-select` 是一个功能强大的下拉选择器组件，支持单选、模糊搜索、自定义选项渲染、虚拟滚动、分页加载、明细弹窗、数字快速定位、多种 UI 风格等功能。通过 `selectdata` 传入数据源，通过 `itemcode` / `itemtext` 指定键值字段。

## 基础用法

```vue
<!-- 基础下拉选择 -->
<zoehis-select v-model="value" :selectdata="options" itemcode="id" itemtext="text"></zoehis-select>

<!-- 可搜索 -->
<zoehis-select v-model="value" :selectdata="options" filterable></zoehis-select>

<!-- 禁用状态 -->
<zoehis-select v-model="value" :selectdata="options" disabled></zoehis-select>

<!-- 自定义选项渲染 -->
<zoehis-select v-model="value" :selectdata="options">
  <template #customItem="{ itemData }">
    <span>{{ itemData.text }} - {{ itemData.code }}</span>
  </template>
</zoehis-select>

<!-- 矩形边框样式 -->
<zoehis-select v-model="value" :selectdata="options" ui-type="rectangle"></zoehis-select>

<!-- 自定义过滤方法 -->
<zoehis-select v-model="value" :selectdata="options" filterable :filter-method="customFilter"></zoehis-select>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| value | — | — | 绑定值（v-model，必填） |
| textvalue | Number / String | — | 文本值 |
| selectdata | Array | [] | 下拉选项数据源 |
| itemcode | String | 'id' | 选项的唯一标识字段名 |
| itemtext | String | 'text' | 选项的显示文本字段名 |
| itemkey | String | — | 选项的 key 字段名，优先级高于 itemcode |
| itemDisabled | String | 'disabled' | 选项的禁用字段名 |
| width | Number / String | 115 | 下拉选择器宽度 |
| placeholder | String | '' | 占位提示文本 |
| disabled | Boolean | false | 是否禁用 |
| clearable | Boolean | true | 是否支持清空 |
| filterable | Boolean | false | 是否支持搜索过滤 |
| filterMethod | Function | — | 自定义模糊查询回调 |
| filterRowData | Function | — | 自定义过滤行数据 |
| filterField | Array | — | 过滤字段列表，默认 [itemtext, itemcode, 'spellCode', 'wbzxCode'] |
| delayTime | String / Number | 200 | 模糊查询延时时间（ms） |
| noMatchText | String | '暂无数据' | 无匹配数据时的提示文本 |
| defaultfirst | Boolean | true | 是否默认选中第一项 |
| noselect | Boolean | false | 是否禁止选中 |
| noClearBlur | Boolean | false | 失焦时是否不清空数据 |
| outclear | String | — | Enter 键时 hoverIndex 在其他位置是否清空数据 |
| beforeSelect | Function | — | 选中前事件，返回 false 阻止选中 |
| beforeClear | Function | — | 清空前事件 |
| renderShowData | Function | — | 自定义选中后显示内容的函数 |
| renderItem | Function | — | 自定义选项渲染内容的函数 |
| scrollToBottom | Function | — | 滚动条滚到底事件回调 |
| scrollToTop | Function | — | 滚动条滚到顶事件回调 |
| dropdownWidth | Number / String | — | 下拉框宽度 |
| dropdownMaxWidth | Number / String | 800 | 下拉框最大宽度 |
| maxHeight | Number / String | — | 下拉列表最大高度 |
| align | String | 'left' | 弹窗对齐方式：left（左对齐）、center（居中）、right（右对齐） |
| placement | — | — | 已废弃，使用 align 替代 |
| popperClass | String | — | 下拉框自定义 class |
| showTextNone | Boolean | false | 文本为空时是否直接显示空 |
| numString | String | — | 支持数字快速定位的字段名 |
| errorTip | String | '' | 错误提示内容 |
| showErrorTip | Boolean | false | 是否始终显示错误提示 |
| preventOverId | String | '' | 错误提示防止被遮挡的容器 id |
| minErrorWidth | String / Number | — | 错误提示最小宽度 |
| imeMode | String | 'disabled' | 原生 ime-mode 属性 |
| uiType | String | '' | UI 样式：默认（下划线）、rectangle（矩形边框）、simple（无边框） |
| iconFont | String | '' | 自定义下拉图标类名 |
| showRefreshBt | Boolean | false | 是否显示刷新按钮 |
| native | Boolean | true | 是否使用原生滚动条 |
| isFocusDropdown | Boolean | true | 聚焦时是否展开下拉 |
| clickselect | Boolean | true | 单击时是否全选文字 |
| validateEvent | Boolean | true | 内部使用，是否触发表单校验事件 |
| textColor | String | — | 文本颜色 |
| closeRz | Boolean | true | 内部临时使用，不建议使用 |

## 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| input | (value) | 选中值改变时触发（v-model） |
| change | (value, item) | 选中值改变时触发 |
| selected | (value, item) | 选中选项时触发（无论值是否改变） |
| clear | — | 清空时触发 |
| focus | — | 获取焦点时触发 |
| blur | — | 失去焦点时触发 |
| enter | — | Enter 键按下时触发 |
| clickicon | (event) | 点击下拉图标时触发 |
| visible-change | (visible, vm) | 下拉框显示/隐藏状态改变时触发 |
| scroll-after | (query, vm) | 滚动后触发 |
| scroll-to-bottom | (query, vm) | 滚动到底部时触发 |
| scroll-to-top | (query, vm) | 滚动到顶部时触发 |
| refresh-bt-click | — | 点击刷新按钮时触发 |
| update:textvalue | (textvalue) | 更新 textvalue 时触发 |

## 方法（Methods）

| 方法名 | 参数 | 说明 |
|--------|------|------|
| focus | (index) | 手动聚焦到选择器，可选指定选项索引 |
| hide | — | 隐藏下拉框 |
| getText | — | 获取当前显示的文本 |
| getSelected | — | 获取当前选中的数据对象 |
| getDisabled | — | 获取是否禁用状态 |
| doDestroy | — | 销毁弹窗 |
| setTextColor | (color) | 设置字体颜色 |
| resetTextColor | — | 重置字体颜色 |
| setSelectedLabel | (val) | 设置显示的文本值 |

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 默认插槽，用于放置 zoehis-option 子组件 |
| customItem | 自定义选项内容，作用域参数：{ itemData } |
