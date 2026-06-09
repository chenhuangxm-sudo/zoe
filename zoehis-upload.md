# zoehis-upload 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

`zoehis-upload` 是一个文件上传组件，支持多种 UI 模式（文本、列表、图片卡片）、拖拽上传、多文件上传、自定义请求、文件列表管理、图片预览等功能。

## 基础用法

```vue
<template>
  <zoehis-upload
    action="/api/upload"
    :file-list="fileList"
    :on-success="handleSuccess"
    :on-error="handleError"
    :before-upload="handleBeforeUpload"
  >
    <zoehis-button type="primary">点击上传</zoehis-button>
    <template slot="tip">
      <p class="el-upload__tip">只能上传jpg/png文件，且不超过500kb</p>
    </template>
  </zoehis-upload>
</template>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| action | String | — | 必选参数，上传地址 |
| headers | Object | {} | 设置上传的请求头部 |
| withcredentials | Boolean | true | 支持发送 cookie 凭证信息 |
| data | Object | — | 上传时附带的额外参数 |
| name | String | 'file' | 上传的文件字段名 |
| multiple | Boolean | false | 是否支持多选文件 |
| accept | String | — | 接受上传的文件类型 |
| disabled | Boolean | false | 是否禁用 |
| drag | Boolean | false | 是否启用拖拽上传 |
| autoupload | Boolean | true | 是否在选取文件后立即上传 |
| showtip | Boolean | true | 是否显示提示 |
| showFileList | Boolean | false | 是否显示已上传文件列表 |
| fileList | Array | [] | 上传的文件列表 |
| uiType | String | 'text' | 文件列表类型：`text`、`list`、`picture-card` |
| size | String | 'big' | 图片卡片尺寸：`big`、`normal`（uiType 为 picture-card 生效） |
| limit | Number | — | 最大允许上传个数 |
| httpRequest | Function | — | 覆盖默认上传行为 |
| beforeupload | Function | — | 上传文件前的钩子 |
| onprogress | Function | noop | 文件上传时的钩子 |
| onsuccess | Function | noop | 文件上传成功时的钩子 |
| onerror | Function | noop | 文件上传失败时的钩子 |
| progressEn | Function | noop | 文件上传时的钩子 |
| successEn | Function | noop | 文件上传成功时的钩子 |
| errorEn | Function | noop | 文件上传失败时的钩子 |
| removeEn | Function | noop | 文件列表移除文件时的钩子 |
| changeEn | Function | noop | 文件状态改变时的钩子 |
| beforeRemove | Function | — | 删除文件前的钩子 |
| exceedEn | Function | noop | 文件超出个数限制时的钩子 |
| beforeSuccess | Function | — | 上传成功前事件，返回 true 显示成功 UI，false 显示失败 UI |
| beforeError | Function | — | 上传失败前事件，返回 true 显示成功 UI，false 显示失败 UI |
| showPreview | Boolean | true | 是否显示预览按钮 |
| beforePreview | Function | — | 预览前事件 |
| previewCustom | Object | {} | 预览弹窗自定义属性（width、height、title） |
| addButtonCustom | Object | {} | 添加按钮自定义属性（width、height） |
| thumbnailCustom | Object | {} | 缩略图自定义属性（width、height） |

## 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| previewClose | file | 预览关闭时触发 |

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 触发上传的按钮或内容 |
| trigger | 触发上传的元素 |
| tip | 上传提示内容 |
| thumbnail | 自定义缩略图（picture-card 模式） |
| thumbnailMask | 自定义缩略图遮罩（picture-card 模式） |
| thumbnailIcon | 自定义缩略图图标（picture-card 模式） |
| preview | 自定义预览内容 |

## 方法（Methods）

| 方法名 | 参数 | 说明 |
|--------|------|------|
| addFile | (file) | 新增文件到列表 |
| delFile | (uid) | 根据 uid 删除文件 |
| getUploadFiles | — | 获取最新的文件列表 |
| abort | (file) | 取消上传 |
| clearFiles | — | 清空文件列表 |
| submit | (file) | 手动上传文件 |
