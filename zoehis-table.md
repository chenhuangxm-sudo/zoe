# zoehis-table 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库  
> 组件名：`zoehisTable`  
> 使用标签：`<zoehis-table>`

---

## 概述

`zoehis-table` 是一个功能丰富的表格组件，支持分页、复选框、序号、行/列拖拽、排序、过滤、分组、固定列、自定义插槽、展开行、表尾合计行等功能。以下从简单到复杂列举使用示例。

---

## 基础用法示例

### 1. 最简单的表格

仅传入 `data`（数据源）和 `configs`（列配置），以及必填的 `keycode`（唯一键字段名）。

```vue
<zoehis-table
  ref="tableRef"
  keycode="id"
  :data="tableData"
  :configs="tableConfigs">
</zoehis-table>
```

```js
// configs 配置示例
tableConfigs: [
  { dataItemCode: 'name', dataItemName: '姓名', itemWidth: '150px' },
  { dataItemCode: 'age', dataItemName: '年龄', itemWidth: '100px' },
  { dataItemCode: 'dept', dataItemName: '科室', itemWidth: '200px' }
]
```

---

### 2. 带序号和复选框的表格

添加 `indexflag` 显示序号列，添加 `checkbox` 启用复选框。

```vue
<zoehis-table
  ref="tableRef"
  keycode="id"
  indexflag
  checkbox
  :data="tableData"
  :configs="tableConfigs"
  @select="handleSelect">
</zoehis-table>
```

```js
// 选中事件回调
handleSelect(selectList, row, rowIndex) {
  console.log('当前选中列表：', selectList);
}
```

---

### 3. 带分页的表格

添加 `pageflag` 开启分页，通过 `page-param` 绑定分页参数，`strip-arr` 配置每页条数选项。

```vue
<zoehis-table
  ref="tableRef"
  keycode="id"
  indexflag
  pageflag
  :data="tableData"
  :configs="tableConfigs"
  :page-param="pageParam"
  :strip-arr="[10, 30, 50, 100]"
  @change-page="changePage"
  @change-strip="changeStrip">
</zoehis-table>
```

```js
data() {
  return {
    pageParam: { total: 0, page: 1, pageSize: 30 }
  };
},
methods: {
  changePage(page) {
    this.pageParam.page = page;
    this.fetchData();
  },
  changeStrip(strip) {
    this.pageParam.pageSize = strip;
    this.pageParam.page = 1;
    this.fetchData();
  }
}
```

---

### 4. 带操作列的表格

添加 `operateflag` 显示操作列，通过 `operate-html` 函数自定义操作按钮 HTML，监听 `operate-click` 事件。

```vue
<zoehis-table
  ref="tableRef"
  keycode="id"
  indexflag
  operateflag
  operatefixed
  operate-align="center"
  :data="tableData"
  :configs="tableConfigs"
  :operate-html="operateHtml"
  @operate-click="operateClickEn">
</zoehis-table>
```

```js
methods: {
  // 构造操作列，通过 data-id 区分不同操作
  operateHtml(item) {
    return "<i data-id='edit' title='编辑' class='zoeIconfont z_bianji_normal'></i>" +
      "<i data-id='delete' title='删除' class='zoeIconfont delete_btn z_bianji_normal'></i>";
  },
  // 操作列点击事件，通过 event.target.dataset.id 判断点击的按钮
  operateClickEn(event, item) {
    const action = event.target.dataset.id;
    if (action === 'edit') {
      this.handleEdit(item);
    } else if (action === 'delete') {
      this.handleDelete(item);
    }
  }
}
```

---

### 5. 自定义单元格插槽

通过 `slot="td_字段名"` 自定义某一列的单元格内容，作用域插槽可获取 `item`（当前行数据）和 `index`（行索引）。

```vue
<zoehis-table
  ref="tableRef"
  keycode="id"
  indexflag
  :data="tableData"
  :configs="tableConfigs">
  <template slot="td_status" slot-scope="{ item }">
    <span :style="{ color: item.status === '1' ? '#00b754' : '#f00f00' }">
      {{ item.status === '1' ? '启用' : '禁用' }}
    </span>
  </template>
  <template slot="td_remark" slot-scope="{ item }">
    <zoehis-input v-model="item.remark" placeholder="请输入备注" ui-type="rectangle" width="100%"></zoehis-input>
  </template>
</zoehis-table>
```

---

### 6. 行拖拽排序

添加 `row-drag-flag` 属性启用行拖拽，监听 `row-drag` 事件获取拖拽结果。

```vue
<zoehis-table
  ref="sortTable"
  :keycode="['sortNo', 'id']"
  indexflag
  :row-drag-flag="true"
  :data="tableData"
  :configs="tableConfigs"
  @row-drag="handleRowDrag">
</zoehis-table>
```

```js
methods: {
  handleRowDrag(index1, index2, row1, row2) {
    console.log('行拖拽完成：', index1, index2);
  }
}
```

---

### 7. 穿梭框中的双表格

配合 `zoehis-transfer` 组件实现左右两个表格的穿梭选择。

```vue
<zoehis-transfer>
  <zoehis-table
    slot="leftMain"
    ref="leftRef"
    indexflag
    checkbox
    keycode="keyCode"
    :data="leftData"
    :configs="leftConfigs"
    :page-param="pageLeftParam"
    :strip-arr="[30, 50, 100, 300, 500]"
    @change-strip="getUndistributedData"
    @change-page="getUndistributedData">
  </zoehis-table>
  <zoehis-table
    slot="rightMain"
    ref="rightRef"
    indexflag
    checkbox
    keycode="keyCode"
    :data="rightData"
    :configs="rightConfigs"
    :page-param="pageRightParam"
    :strip-arr="[30, 50, 100, 300, 500]"
    @change-strip="getDistributedData"
    @change-page="getDistributedData">
  </zoehis-table>
</zoehis-transfer>
```

---

### 8. 带过滤功能的表格

添加 `filterflag` 开启过滤弹窗，通过 `filterConfig` 配置过滤字段。

```vue
<zoehis-table
  ref="tableRef"
  keycode="id"
  indexflag
  filterflag
  :data="tableData"
  :configs="tableConfigs"
  :filter-config="filterConfig"
  @confirm-filter="confirmFilter">
</zoehis-table>
```

---

### 9. 隐藏列功能

添加 `hide-column-flag` 开启列显隐控制，用户可通过下拉菜单选择显示/隐藏列。

```vue
<zoehis-table
  ref="tableRef"
  keycode="id"
  indexflag
  hide-column-flag
  :data="tableData"
  :configs="tableConfigs">
</zoehis-table>
```

---

### 10. 展开行

添加 `expand-flag` 启用展开行功能，通过 `expand` 插槽自定义展开内容。

```vue
<zoehis-table
  ref="tableRef"
  keycode="id"
  indexflag
  expand-flag
  :data="tableData"
  :configs="tableConfigs">
  <template slot="expand" slot-scope="{ item }">
    <div style="padding: 10px;">
      <p>详细信息：{{ item.detail }}</p>
    </div>
  </template>
</zoehis-table>
```

---

### 11. 分组表格

添加 `mergeflag` 开启分组功能，通过 `mergeRow` 插槽自定义分组行内容，`mergeChildren` 插槽自定义子行内容。

```vue
<zoehis-table
  ref="tableRef"
  keycode="id"
  mergeflag
  :data="tableData"
  :configs="tableConfigs">
  <template slot="mergeRow" slot-scope="{ item }">
    <strong>{{ item.groupName }}</strong>
  </template>
  <template slot="mergeChildren" slot-scope="{ item }">
    <!-- 自定义子行内容 -->
  </template>
</zoehis-table>
```

---

### 12. 表尾合计行

添加 `show-summary` 开启表尾合计，通过 `summary-method` 方法自定义合计逻辑。

```vue
<zoehis-table
  ref="tableRef"
  keycode="id"
  indexflag
  show-summary
  :data="tableData"
  :configs="tableConfigs"
  :summary-method="summaryMethod">
</zoehis-table>
```

```js
methods: {
  summaryMethod({ data, config }) {
    const totals = [];
    config.forEach((item, index) => {
      if (item.dataItemCode === 'amount') {
        totals[index] = data.reduce((sum, row) => sum + Number(row.amount || 0), 0);
      } else {
        totals[index] = index === 0 ? '合计' : '';
      }
    });
    return totals;
  }
}
```

---

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| data | Array | `[]` | 表格数据源 |
| configs | Array | `[]` | 列配置数组，每项包含 `dataItemCode`(字段名)、`dataItemName`(列标题)、`itemWidth`(列宽) 等 |
| keycode | String / Array | `'uiKeyCode'` | 数据唯一键字段名，支持多字段组合（传数组） |
| pageflag | Boolean | `false` | 是否启用分页 |
| page-param | Object | `{ total: 0, page: 1, pageSize: 30 }` | 分页参数 |
| strip-arr | Array | `[10, 20, 30, 40]` | 每页条数选项 |
| indexflag | Boolean | `false` | 是否显示序号列 |
| indexfixed | Boolean | `false` | 序号列是否左固定 |
| index-width | String | `'50px'` | 序号列宽度 |
| checkbox | Boolean | `false` | 是否显示复选框 |
| checkboxfixed | Boolean | `false` | 复选框是否左固定 |
| checkbox-width | String | `'50px'` | 复选框列宽度 |
| operateflag | Boolean | `false` | 是否显示操作列 |
| operatefixed | Boolean | `false` | 操作列是否右固定 |
| operate-width | String | `'100px'` | 操作列宽度 |
| operate-html | Function | - | 自定义操作列 HTML 内容的函数 `(row, rowIndex) => string` |
| operate-text | String | `'操作'` | 操作列表头文本 |
| operate-align | String | `'left'` | 操作列文本对齐方式 |
| drag-flag | Boolean | `false` | 是否允许列拖拽 |
| row-drag-flag | Boolean | `false` | 是否允许行拖拽 |
| before-row-drag | Function | - | 行拖拽前回调，返回 `false` 阻止拖拽 |
| mergeflag | Boolean | `false` | 是否启用分组 |
| expand-flag | Boolean | `false` | 是否启用展开行 |
| expand-width | String | `'38px'` | 展开行图标列宽度 |
| expand-icon-col | Boolean | `true` | 是否显示展开行图标列 |
| expand-bg-color | String | `''` | 展开行背景色 |
| show-summary | Boolean | `false` | 是否显示表尾合计行 |
| summary-method | Function | - | 合计行回调方法 `({ data, config }) => array` |
| span-method | Function | - | 合并行/列的方法 |
| do-filter-func | Function | - | 自定义过滤器函数 `(val, row, config) => string` |
| render-attr | Array | `[]` | 需要自定义渲染的字段名数组 |
| render-html | Function | - | 自定义渲染 HTML 函数 |
| sort-attr | Array | `[]` | 需要自定义排序的字段名数组 |
| do-sort-func | Function | - | 自定义排序函数 |
| comb-sort | Boolean | `false` | 是否启用组合排序 |
| clear-sort-flag | Boolean | `false` | 是否开启取消排序 |
| filterflag | Boolean | `false` | 是否启用过滤弹窗 |
| filter-config | Object | - | 过滤配置 |
| hide-column-flag | Boolean | `false` | 是否启用隐藏列功能 |
| header-flag | Boolean | `true` | 是否显示表头 |
| boxborder | Boolean | `true` | 是否显示表格上下边框 |
| select-num | Boolean | `false` | 是否显示当前选中条数 |
| show-all-checkbox-flag | Boolean | `true` | 是否显示全选复选框 |
| disabled-all-checkbox | Boolean | `false` | 是否禁用全选复选框 |
| checkbox-disabled | Boolean | `false` | 是否全部禁用复选框 |
| row-click-select-checkbox | Boolean | `false` | 单击行时是否选择复选框 |
| shift-select-flag | Boolean | `false` | 是否开启 Shift 多选 |
| before-row-click | Function | - | 行点击前回调 |
| before-select | Function | - | 某行复选前回调 |
| before-select-all | Function | - | 全选前回调 |
| row-class-name | Function / String | - | 行自定义 class |
| row-style | Function / Object | - | 行自定义样式 |
| th-class-name | String | `''` | 表头 th 自定义 class |
| supportkey | Boolean | `false` | 是否支持上下快捷键 |
| zoomable | Boolean | `false` | 是否可缩放（Ctrl+滚轮） |
| zoom-factor | Number | `0.02` | 缩放系数 |
| min-zoom | Number | `0.5` | 最小缩放比 |
| max-zoom | Number | `2` | 最大缩放比 |
| user-behavior | Boolean | `false` | 是否本地存储用户行为（列显隐等） |
| key-storage | String | `''` | 用户行为存储的 key |
| save-user-behavior-btn | Boolean | `false` | 是否显示存储用户行为保存按钮 |
| swap-row-flag | Boolean | `false` | 是否使用交换行（排序） |
| swap-row-width | String | `'120px'` | 交换行列宽度 |
| auto-row-height | Boolean | `false` | 行高是否按内容撑开 |
| show-ellipsis | Boolean | `false` | 数据超出宽度是否显示省略号 |
| showtotal | Boolean | `true` | 是否显示分页总数 |
| is-set-strip | Boolean | `true` | 分页组件是否显示"每页显示条数" |
| merge-row-operate | Boolean | `false` | 自定义分组行时是否保留操作列 |
| merge-accordion | Boolean | `false` | 分组切换是否只显示一个（手风琴模式） |
| merge-icon | Boolean | `true` | 分组是否显示切换按钮 |
| dblclick-show-child | Boolean | `true` | 双击是否切换显示子元素 |
| check-strictly | Boolean | `false` | 复选框是否与父节点严格关联 |
| click-currow-keycode | String | - | 点击当前行，根据此配置的 code 选中相同数据 |
| allow-mouse-wheel | String | `''` | 是否允许滚动，`'vertical'` 只允许垂直滚动 |
| exchange-column-flag | Boolean | `true` | 列拖拽是否交换模式 |
| exchange-row-flag | Boolean | `true` | 行拖拽是否交换模式 |
| excel-version | String | `'default'` | 导出 Excel 版本，`'compatible'` 为兼容版（2003） |
| summary-class-name | String | `''` | 自定义合计行 className |
| no-summary-border-code | Array | `[]` | 合并行列无边框 code 数组 |
| reset-scoll | Boolean | `true` | data 改变时是否重置滚动条位置 |
| delay-time | Number | `0` | 延迟时间 |
| samefilter | Boolean | `true` | 过滤条件是否可选择多个相同列名 |
| operator-list | Array | `[{id: '=', text: '模糊查询'}]` | 过滤操作符列表 |
| user-filter-temp | Boolean | `false` | 是否开启用户过滤模板 |
| cud-filter-template-data | Function | - | 用户过滤模板增删改查方法 |
| filter-dlg-soft | Boolean | `true` | 过滤弹窗中是否显示排序 |
| deal-format | Boolean | `true` | 是否默认处理成后端需要的格式 |
| append-index | Boolean | - | 序号是否追加（分页时序号连续） |

---

## 方法（Methods）

通过 `$refs` 调用，例如 `this.$refs.tableRef.setZoom(1)`。

| 方法名 | 参数 | 说明 |
|--------|------|------|
| setZoom | `(size: Number)` | 设置表格缩放比例（需启用 `zoomable`） |
| setSort | `(dataItemCode: String, type: 'up'\|'down')` | 手动触发某列排序 |
| clearSortEn | `(d: Object)` | 清除某列的排序状态 |
| clearSortState | - | 清除所有列的排序状态 |
| getCombSortMap | - | 获取组合排序的 Map |
| setCombSortMap | `(sortArr: Array, triggerEvent: Boolean)` | 设置组合排序 |
| doSelectAll | `(flag: Boolean)` | 全选/取消全选 |
| getSelectedMap | - | 获取当前选中的行数据 Map |
| setRowDisabled | `(row: Object, disabled: Boolean)` | 设置某行复选框禁用状态 |
| getRowKey | `(row: Object)` | 获取某行的唯一键值 |
| changeWidthByColumn | `(column: Object, width: String, oldWidth: String)` | 修改某列宽度 |
| toggleCol | `(col: Object, validFlag: String)` | 切换某列的显示/隐藏 |
| toggleColAdjustTable | - | 切换列后调整表格 |
| setAideColumnSelectAllVal | `(val: String)` | 设置隐藏列全选值 |
| getExcelHead | `(config: Array)` | 获取 Excel 导出的表头配置 |
| getDropConfigs | - | 获取列拖拽后的配置信息 |
| openFilter | `(clearFlag: Boolean)` | 打开过滤弹窗 |
| initFilterSelectVal | `(dataItemCode: String)` | 初始化过滤选中值 |
| getFixedFormatData | `(conditions: Array)` | 获取格式化后的过滤条件数据 |
| clearFilterList | - | 清空过滤条件列表 |
| closeFilter | - | 关闭过滤弹窗 |
| mainScrollMove | `(axis: {top: Number, left: Number})` | 主表格滚动到指定位置 |
| resizeBox | - | 重新计算表格尺寸 |
| changeBodyHeight | - | 更新表格主体高度 |
| updateScrollbar | - | 更新滚动条状态 |
| selectRange | `(start: Number, end: Number)` | 选中指定范围的行（需启用 Shift 多选） |
| setClickSelectKeyCode | `(row: Object)` | 设置点击选中行的 keycode |

---

## 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| row-click | `(row, event, rowIndex, params)` | 行点击时触发 |
| row-dblclick | `(row, event, rowIndex, params)` | 行双击时触发 |
| row-contextmenu | `(data, event)` | 行右键菜单时触发 |
| row-keydown | `({ row, rowIndex }, event)` | 键盘上下键切换行时触发 |
| row-drag | `(index1, index2, row1, row2)` | 行拖拽完成时触发 |
| operate-click | `(event, row, rowIndex, params)` | 操作列点击时触发 |
| select | `(selectList, row, rowIndex, params)` | 复选框选中/取消时触发 |
| select-all | `(selectList, isSelected)` | 全选/取消全选时触发 |
| select-num | `(num: Number)` | 已选条数变化时触发 |
| change | `(val: Array)` | 表格数据变化时触发 |
| change-page | `(page: Number)` | 分页页码变化时触发 |
| change-strip | `(strip: Number)` | 每页条数变化时触发 |
| sort-change | `(config, type)` | 排序变化时触发 |
| default-sort-change | `(config, type)` | 默认排序变化时触发 |
| comb-sort-change | `(sortArr: Array)` | 组合排序变化时触发 |
| clear-sort | `(config)` | 取消排序时触发 |
| col-click | `(params)` | 单元格点击时触发 |
| col-dblclick | `(params)` | 单元格双击时触发 |
| swap-row-click | `(event, row, rowIndex, direction)` | 交换行按钮点击时触发 |
| column-drag | `(column, width, newWidth, oldWidth)` | 列拖拽调整宽度时触发 |
| drop-change | `(configs: Array)` | 列拖拽交换后触发 |
| handle-drag-start | `(event, rowData)` | 行拖拽开始时触发 |
| drop-tr-ev | `(event, rowData, newIndex)` | 外部行拖入表格时触发 |
| scrollafter | `(scrollTarget)` | 表格滚动后触发 |
| expandEn | `(row, rowIndex, expanded)` | 展开行切换时触发 |
| th-contextmenu | `(event, columnConfig)` | 表头右键菜单时触发 |
| zoom-table | `(zoom: Number)` | 表格缩放时触发 |
| table-mousewheel | `(event)` | 表格滚轮事件时触发 |
| confirm-filter | `(filterData)` | 过滤确认时触发 |
| close-filter | - | 过滤弹窗关闭时触发 |
| hanle-toggle | - | 列显隐切换时触发 |
| save-user-behavior | - | 保存用户行为时触发 |

---

## 插槽（Slots）

| 插槽名 | 作用域参数 | 说明 |
|--------|-----------|------|
| `td_{dataItemCode}` | `{ item, index, currentIndex, parentRow, parentIndex }` | 自定义单元格内容，`dataItemCode` 为字段名 |
| `th_{dataItemCode}` | - | 自定义表头内容 |
| `{dataItemCode}` | - | 自定义表头附加内容（位于表头插槽下方） |
| `expand` | `{ item, index, currentIndex }` | 展开行内容（需启用 `expand-flag`） |
| `empty` | - | 空数据时的占位内容 |
| `statistics` | - | 表格底部统计区域 |
| `tableSelectNum` | `{ num }` | 已选条数自定义显示 |
| `mergeRow` | `{ item, index, currentIndex }` | 自定义分组行内容（需启用 `mergeflag`） |
| `mergeChildren` | `{ item, index, currentIndex }` | 自定义分组子行内容 |
| `showSecond` | `{ item, index, currentIndex }` | 分组展开图标自定义 |
| `hideSecond` | `{ item, index, currentIndex }` | 分组收起图标自定义 |
| `summary_{dataItemCode}` | `{ item }` | 自定义合计行某列内容 |
| `summary_checkboxkey` | `{ item }` | 自定义合计行复选框列内容 |
| `summary_swaprowkey` | `{ item }` | 自定义合计行交换行列内容 |
| `summary_operatekey` | `{ item }` | 自定义合计行操作列内容 |

---

## 列配置（configs 配置项）

`configs` 数组每项支持的属性：

| 属性名 | 类型 | 说明 |
|--------|------|------|
| dataItemCode | String | **必填**，字段名，对应 data 中的属性 |
| dataItemName | String | **必填**，列标题文本 |
| itemWidth | String | **必填**，列宽度，如 `'150px'` |
| sortNo | Number | 列排序序号，数值越小越靠左 |
| dataItemSort | String | 是否可排序，`'1'` 为可排序 |
| dataTextAlign | String | 数据对齐方式，`'left'`/`'center'`/`'right'`，默认 `'center'` |
| headTextAlign | String | 表头对齐方式，`'left'`/`'center'`/`'right'`，默认 `'center'` |
| fixedFlag | String | 固定列，`'left'` 左固定，`'right'` 右固定 |
| filterType | String | 过滤器类型，`'other'` 自定义，或时间格式字符串 |
| validFlag | String | 列是否显示，`'1'` 显示，`'0'` 隐藏（配合隐藏列功能） |
| uiIndexFlag | Boolean | 是否为序号列 |
| uiColspan | Number | 跨列数（合并表头） |
| showEllipsis | Boolean | 超出宽度是否显示省略号 |
| dragFlag | Boolean | 是否允许拖动该列 |
| hideOperate | Boolean | 是否显示隐藏列操作按钮 |
| titleEdit | Boolean | 列标题是否可编辑 |

---

## 使用说明

1. **keycode 必须配置**：`keycode` 是表格数据的唯一标识，不配置会有警告。支持多字段组合（传数组）。
2. **configs 中的 itemWidth 建议配置**：每列的宽度建议明确设置，否则可能出现列宽异常。
3. **数据更新**：修改 `data` 数组后表格会自动重新渲染。
4. **自定义过滤器**：通过 `do-filter-func` 或 `configs` 中的 `filterType` 控制数据展示格式。
5. **行/列拖拽**：需要分别设置 `row-drag-flag` 和 `drag-flag`。
6. **用户行为存储**：启用 `user-behavior` 并配置 `key-storage`，可持久化列显隐、列顺序等用户设置。
