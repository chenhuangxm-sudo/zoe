# zoehis-autocomplete 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

自动完成/自动补全输入框组件。支持远程搜索、键盘导航、下拉滚动分页、自定义选项渲染、多种对齐方式等功能。基于 `zoehis-input` 和 `zoehis-autocomplete-suggestions` 实现。

## 基础用法

```vue
<zoehis-autocomplete
  v-model="value"
  :fetchSuggestions="querySearch"
  placeholder="请输入内容"
  @select="handleSelect"
>
</zoehis-autocomplete>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| value | - | '' | 绑定值，支持 v-model |
| width | Number/String | 115 | 输入框宽度 |
| dropdownWidth | Number/String | - | 下拉弹窗宽度 |
| dropdownMaxWidth | Number/String | 800 | 下拉弹窗最大宽度 |
| triggerOnFocus | Boolean | true | 是否在输入框 focus 时显示建议列表 |
| hideLoading | Boolean | - | 是否隐藏远程加载时的加载图标 |
| delayTime | Number | 200 | 获取输入建议的去抖延时（毫秒） |
| highlightFirstItem | Boolean | false | 是否默认高亮远程搜索建议中的第一项 |
| popperClass | String | - | 下拉列表的类名 |
| fetchSuggestions | Function | - | 返回输入建议的方法，通过 callback(data:[]) 返回 |
| preventOverId | String | '' | 弹出框插入的容器 ID |
| dropdownSearch | Boolean | false | 是否显示下拉框的搜索 |
| popperOptions | Object | - | 弹出框配置信息 |
| align | String | 'left' | 弹出窗对齐方式：left / center / right |
| itemtext | String | 'text' | 推荐列表显示文本的字段名 |
| itemcode | String | 'id' | 推荐列表显示 ID 的字段名 |
| selectWhenUnmatched | Boolean | false | 输入无匹配时是否触发 select 事件 |
| scrollAppendData | Function | - | 滚动分页追加数据方法 |
| disabled | Boolean | - | 是否禁用 |
| renderSelectData | Function | - | 自定义选中值在输入框中的显示内容 |
| clickselect | Boolean | false | 是否点击即选中 |
| uiType | String | '' | UI 样式类型（默认下划线，rectangle 矩形边框） |
| multiple | Boolean | false | 是否多选模式 |

## 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| input | (value) | 输入值变化时触发 |
| change | (value) | 值改变时触发 |
| select | (item) | 选中建议项时触发 |
| focus | (event) | 输入框获得焦点时触发 |
| blur | (event) | 输入框失去焦点时触发 |
| clear | (event) | 清空输入时触发 |
| clickicon | (event) | 点击图标时触发 |
| inputnative | (value) | 原生 input 事件触发 |

## 方法（Methods）

| 方法名 | 参数 | 说明 |
|--------|------|------|
| focus | - | 使输入框获得焦点 |
| getValue | - | 获取输入框的值 |
| setValue | - | 设置输入框的值 |
| getDisabled | - | 获取是否禁用状态 |
| close | - | 关闭建议列表 |

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 自定义建议项渲染，作用域插槽，参数 `{ item, index }` |
