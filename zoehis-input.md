# zoehis-input 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

`zoehis-input` 是一个功能全面的输入框组件，支持文本输入、密码输入、文本域（textarea）三种类型。提供清空、正则校验、数字/浮点数/整数校验、错误提示、输入长度限制、防抖、复制粘贴、自定义图标等多种功能。

## 基础用法

```vue
<!-- 基础文本输入框 -->
<zoehis-input v-model="value" placeholder="请输入"></zoehis-input>

<!-- 密码输入框 -->
<zoehis-input v-model="value" type="password"></zoehis-input>

<!-- 文本域 -->
<zoehis-input v-model="value" type="textarea"></zoehis-input>

<!-- 禁用状态 -->
<zoehis-input v-model="value" disabled></zoehis-input>

<!-- 带图标 -->
<zoehis-input v-model="value" icon="z_search_normal"></zoehis-input>

<!-- 数字校验 -->
<zoehis-input v-model="value" check-type="float" :decimal-length="2"></zoehis-input>

<!-- 错误提示 -->
<zoehis-input v-model="value" error-tip="请输入正确的格式"></zoehis-input>

<!-- 复合型输入框 -->
<zoehis-input v-model="value">
  <template #prepend><span>前缀</span></template>
  <template #append><span>后缀</span></template>
</zoehis-input>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| type | String | 'text' | 输入框类型：text（文本）、password（密码）、textarea（文本域）、suffix（后缀型） |
| value | — | '' | 绑定值（v-model） |
| icon | String | — | 自定义图标类名 |
| disabled | Boolean | false | 是否禁用 |
| readonly | Boolean | false | 是否只读 |
| placeholder | String | — | 占位提示文本 |
| width | Number / String | 115（text/suffix 时为 '100%'） | 输入框宽度 |
| height | Number / String | '' | 输入框高度 |
| clearable | Boolean | true | 是否启用清空功能 |
| clickselect | Boolean | true | 单击时是否全选文字 |
| textAlign | String | 'left' | 文本对齐方式 |
| maxlength | Number / String | '' | 原生 maxlength 属性 |
| showclose | Boolean | false | 有清空功能时是否优先显示 X 图标 |
| reg | RegExp | — | 自定义正则校验 |
| checkType | String | — | 校验类型：num（正整数）、int（整数）、float（浮点数）、digit（纯数字）、english（纯英文） |
| decimalLength | Number | — | 保留的小数位数 |
| digitLength | Number | — | 保留的正数位数 |
| positive | Boolean | false | 是否为正数（含 0） |
| checkzero | Boolean | true | 校验时是否包含 0 |
| deleteKey | Boolean | false | 是否支持 Delete 快捷键清空 |
| delayTime | String / Number | 0 | 输入防抖延时时间（ms） |
| beforeClear | Function | — | 清空前事件，返回 false 阻止清空 |
| errorTip | String | '' | 错误提示内容，为空时关闭错误提示 |
| showErrorTip | Boolean | false | 是否始终显示错误提示（不受聚焦状态影响） |
| preventOverId | String | '' | 错误提示防止被遮挡的容器元素 id |
| minErrorWidth | String / Number | — | 错误提示最小宽度 |
| imeMode | String | 'auto' | 原生 ime-mode 属性（输入法引擎） |
| firstChange | Boolean | false | true 表示初始化不触发 change 事件 |
| copyAndPasteFlag | Boolean | false | 是否开启右键复制粘贴功能（需壳环境支持） |
| isIconStacking | Boolean | true | 内部使用，X 按钮和向下箭头是否叠放 |
| uiType | String | '' | UI 样式：rectangle（矩形输入框）、onlyBottom（仅底部边框） |
| textColor | String | — | 文本颜色 |
| autosize | Boolean / Object | false | 文本域自适应高度，可传 { minRows, maxRows } |
| limitLength | Number / String | — | 文本域限制字节长度（中文算两个字节） |
| validateEvent | Boolean | true | 内部使用，是否触发表单校验事件 |
| closeRz | Boolean | true | 内部临时使用，不建议使用 |

## 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| input | (value) | 输入值改变时触发（v-model） |
| inputnative | (value) | 原生 input 事件 |
| change | (value) | 值改变时触发 |
| focus | (event) | 获取焦点时触发 |
| blur | (event) | 失去焦点时触发 |
| click | (event) | 点击输入框时触发 |
| clear | (event) | 清空内容时触发 |
| clickicon | (event) | 点击图标时触发 |
| mousedownIcon | (event) | 图标鼠标按下时触发 |
| mousedownClear | (event) | 清空按钮鼠标按下时触发 |
| keyup | (event) | 键盘弹起时触发 |
| compositionstart | (event) | 输入法开始输入时触发 |
| compositionupdate | (event) | 输入法输入更新时触发 |
| compositionend | (event) | 输入法输入结束时触发 |

## 方法（Methods）

| 方法名 | 参数 | 说明 |
|--------|------|------|
| focus | — | 手动聚焦到输入框，clickselect 为 true 时同时全选 |
| getValue | — | 获取当前输入框的值 |
| setValue | (val) | 设置输入框的值 |
| getDisabled | — | 获取是否禁用状态 |
| getInput | — | 获取原生 input/textarea 元素 |
| inputSelect | — | 全选输入框内容 |
| setTextColor | (color) | 设置字体颜色 |
| resetTextColor | — | 重置字体颜色 |
| setPlacementToError | — | 重新设置错误提示的位置 |
| setErrorTipWidth | — | 重新设置错误提示宽度 |

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| prepend | 复合型输入框的前缀内容 |
| append | 复合型输入框的后缀内容 |
