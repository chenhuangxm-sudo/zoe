# zoehis-simple-table 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

简易表格组件，支持虚拟滚动、列拖拽排序、列宽调整、复选框多选、排序（前端/后端）、列隐藏、过滤弹窗、分页等功能。适用于大数据量列表展示场景。

## 基础用法

```vue
<zoehis-simple-table
  :data="tableData"
  :configs="tableConfig"
  keycode="id"
  :pageflag="true"
  :pageParam="pageParam"
  @row-click="handleRowClick"
  @change-page="handleChangePage"
  @change-strip="handleChangeStrip"
>
</zoehis-simple-table>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| data | Array | [] | 表格数据 |
| configs | Array | [] | 表格列配置信息 |
| keycode | Array/String | (required) | 数据行的唯一标识字段名 |
| dragFlag | Boolean | - | 是否允许列拖动 |
| showAllCheckboxFlag | Boolean | true | 是否显示全选复选框 |
| doFilterFunc | Function | - | 自定义过滤器函数 |
| dealFormat | Boolean | true | 是否默认处理成后端需要的格式 |
| filterDlgSoft | Boolean | true | 是否在过滤弹窗中显示排序 |
| keyStorage | String | '' | 本地存储 key |
| filterConfig | Object | - | 过滤配置 |
| cudFilterTemplateData | Function | null | 用户过滤模板数据 |
| userFilterTemp | Boolean | false | 是否开启用户过滤模板 |
| filterflag | Boolean | false | 是否启用过滤弹窗功能 |
| checkboxDisabled | Boolean | - | 是否全部禁用复选框 |
| beforeSelectAll | Function | - | 全选前方法 |
| beforeSelect | Function | - | 某行复选前方法 |
| beforeRowClick | Function | - | 行点击前方法 |
| thClassName | String | - | 表头 th 的自定义 class |
| checkbox | Boolean | - | 是否使用复选框 |
| checkboxWidth | String | '50px' | 复选框列宽度 |
| indexWidth | String | '50px' | 序号列宽度 |
| indexflag | Boolean | - | 是否需要序号列 |
| pageflag | Boolean | - | 是否显示分页 |
| pageParam | Object | {total:0, page:1, pageSize:2000} | 分页参数 |
| stripArr | Array | [10,20,30,40,2000] | 分页每页条数配置 |
| isSetStrip | Boolean | true | 是否可设置每页条数 |
| showtotal | Boolean | true | 是否显示分页总数 |
| hideColumnFlag | Boolean | - | 是否启用隐藏列功能 |
| sortAttr | Array | [] | 自定义排序字段集合 |
| selectNum | Boolean | - | 是否显示当前选中条数 |
| combSort | Boolean | false | 是否启用组合排序 |
| rowClassName | Function/String | - | 行自定义 class |
| clearSortFlag | Boolean | false | 是否开启取消排序 |
| userBehavior | Boolean | false | 是否本地存储用户行为 |

## 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| row-click | (row, event, rowIndex, params) | 行点击时触发 |
| row-dblclick | (row, event, rowIndex, params) | 行双击时触发 |
| select | (selectList, row, rowIndex, params) | 复选框选中状态变化时触发 |
| select-all | (selectList, val) | 全选/取消全选时触发 |
| change-strip | (val) | 每页条数变化时触发 |
| change-page | (val) | 页码变化时触发 |
| sort-change | (column, order) | 自定义排序时触发 |
| default-sort-change | (column, order) | 默认排序变化时触发 |
| comb-sort-change | (sortArr) | 组合排序变化时触发 |
| clear-sort | (column) | 取消排序时触发 |
| confirm-filter | (filterData) | 过滤确认时触发 |
| close-filter | - | 关闭过滤弹窗时触发 |
| columnDrag | (column, newWidth, width, oldWidth) | 列宽拖动调整时触发 |
| drop-change | (configs) | 列拖拽排序后触发 |
| scrollafter | (event) | 滚动时触发 |
| hanle-toggle | - | 隐藏/显示列操作后触发 |

## 方法（Methods）

| 方法名 | 参数 | 说明 |
|--------|------|------|
| getData | - | 获取当前表格数据 |
| getSelectArr | (disabledFlag) | 获取复选框选中的值 |
| getSelectFlag | (data) | 获取某行复选框选中状态 |
| getCurrentRow | - | 获取当前选中行 |
| getConfigs | - | 获取表格最新配置信息 |
| getCombSortMap | - | 获取组合排序数据 |
| setCurrentRow | (row) | 设置某行为选中行 |
| toggleRowSelection | (row, selected) | 切换某行选中状态 |
| toggleMultiRowSelection | (multiRow, selected) | 切换多行选中状态 |
| toggleAllRowSelection | (flag) | 全选/清空全选 |
| setRowDisabled | (row, disabled) | 设置行复选框不可点击 |
| scrollMove | (axis) | 设置滚动条滚动位置 |
| scrollSpecRow | (curRow, isSelect, callback) | 表格滚动到指定行 |
| scrollSpecCol | (curCol) | 表格滚动到指定列 |
| clearSortState | - | 清空当前排序状态 |
| setCombSortMap | (sortArr, triggerEvent) | 设置头部组合排序 |
| openFilter | (clearFlag) | 打开过滤弹窗 |
| closeFilter | - | 关闭过滤弹窗 |
| clearFilterList | - | 清空过滤数据 |
| initTemplate | (template) | 初始化过滤模板 |
| getTemplateData | - | 获取过滤模板信息 |
| inverseSelection | - | 反选复选框 |
| getDropConfigs | - | 获取拖拽后的配置信息 |

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| th_{dataItemCode} | 自定义表头内容，如 `th_name` |
| {dataItemCode} | 自定义列内容，如 `name` |
| empty | 空数据时的展示内容 |
| tableSelectNum | 已选条数提示区域，作用域插槽，参数 `{ num }` |
