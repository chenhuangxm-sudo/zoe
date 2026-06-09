# zoehis-cascader 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

`zoehis-cascader` 是一个级联选择器组件，支持单选/多选、懒加载、可搜索过滤、自定义节点渲染、路径分隔符、父子不关联选择、多种 UI 风格等功能。适用于地区选择、分类选择等层级数据场景。

## 基础用法

```vue
<!-- 基础级联选择 -->
<zoehis-cascader v-model="value" :options="options"></zoehis-cascader>

<!-- 可搜索 -->
<zoehis-cascader v-model="value" :options="options" filterable></zoehis-cascader>

<!-- 多选 -->
<zoehis-cascader v-model="value" :options="options" :configs="{ multiple: true }"></zoehis-cascader>

<!-- 父子不关联 -->
<zoehis-cascader v-model="value" :options="options" :configs="{ checkStrictly: true }"></zoehis-cascader>

<!-- 自定义分隔符 -->
<zoehis-cascader v-model="value" :options="options" separator=" > "></zoehis-cascader>

<!-- 懒加载 -->
<zoehis-cascader v-model="value" :lazy="true" :lazy-load="lazyLoadFn"></zoehis-cascader>

<!-- 自定义节点 -->
<zoehis-cascader v-model="value" :options="options">
  <template v-slot="{ node, data }">
    <span>{{ data.label }} - {{ data.code }}</span>
  </template>
</zoehis-cascader>

<!-- 矩形边框样式 -->
<zoehis-cascader v-model="value" :options="options" ui-type="rectangle"></zoehis-cascader>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| value | — | — | 绑定值（v-model） |
| options | Array | — | 级联选项数据源 |
| configs | Object | — | 配置对象，可覆盖以下默认配置 |
| configs.expandTrigger | String | 'click' | 展开方式：click（点击）、hover（悬停） |
| configs.multiple | Boolean | false | 是否多选 |
| configs.checkStrictly | Boolean | false | 父子是否不关联 |
| configs.emitPath | Boolean | true | 是否返回路径 |
| configs.lazy | Boolean | false | 是否懒加载 |
| configs.lazyLoad | Function | — | 懒加载函数 |
| configs.key | String | 'key' | 节点 key 字段名 |
| configs.value | String | 'value' | 节点 value 字段名 |
| configs.label | String | 'label' | 节点 label 字段名 |
| configs.children | String | 'children' | 节点 children 字段名 |
| configs.leaf | String | 'leaf' | 节点 leaf 字段名 |
| configs.disabled | String | 'disabled' | 节点 disabled 字段名 |
| width | String / Number | 160 | 组件宽度 |
| placeholder | String | — | 占位提示文本 |
| disabled | Boolean | false | 是否禁用 |
| separator | String | '/' | 选项内路径分隔符 |
| limit | String | ',' | 多选时各选项间分隔符 |
| showAllLevels | Boolean | true | 是否显示完整路径 |
| clearable | Boolean | true | 是否支持清空 |
| filterable | Boolean | false | 是否支持搜索过滤 |
| filterMethod | Function | — | 自定义过滤函数 |
| beforeFilter | Function | () => Promise.resolve() | 过滤前方法，返回 false 阻止过滤 |
| emptyText | String | '' | 搜索无数据时的提示文本 |
| debounce | Number | 200 | 搜索防抖时间（ms） |
| iconFont | String | — | 自定义下拉图标类名 |
| uiType | String | — | UI 样式：默认（下划线）、rectangle（矩形边框） |
| align | String | 'left' | 弹窗对齐方式：left、center、right |
| placement | String | 'bottom-start' | 弹窗位置 |
| offsetXY | Array | [0, 6] | 弹窗偏移量 |

## 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| input | (value) | 选中值改变时触发（v-model） |
| change | (value, checkedNodes) | 选中值改变时触发 |
| blur | (event) | 输入框失去焦点时触发 |
| focus | (event) | 输入框获取焦点时触发 |
| visible-change | (visible) | 面板显示/隐藏状态改变时触发 |
| expand-change | (node) | 展开节点时触发 |
| active-item-change | (node) | 激活节点时触发 |
| clear | — | 清空时触发 |
| scroll-after | (e, node) | 滚动后触发 |
| scroll-to-bottom | (e, node) | 滚动到底部时触发 |
| scroll-to-top | (e, node) | 滚动到顶部时触发 |

## 方法（Methods）

| 方法名 | 参数 | 说明 |
|--------|------|------|
| clear | — | 清空选中 |
| getCheckedNodes | (leafOnly) | 获取选中节点数组 |
| getCurrentCheckedNodes | — | 获取当前选中节点数组 |
| appendNode | (pKey, newNodeData) | 在指定父节点下新增子节点 |
| removeNode | (nodeKey) | 移除指定节点 |
| setNodeStatusByKey | (key, val) | 根据 key 设置节点选中状态 |
| setValueStatusByValue | (value, val) | 根据 value 设置节点选中状态 |
| focusFirstNode | — | 聚焦到第一个节点 |

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 自定义节点内容，作用域参数：{ node, data } |
| searchNode | 自定义搜索列表节点内容，作用域参数：{ node } |
| empty | 搜索无数据时的自定义空状态内容 |
