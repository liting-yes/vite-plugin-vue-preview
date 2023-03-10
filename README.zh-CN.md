<h1 align="center">vite-plugin-vue-preview</h1>

<p align="center">
  <a href="https://www.npmjs.com/package/vite-plugin-vue-preview"><img src="https://img.shields.io/npm/dm/vite-plugin-vue-preview" alt="Downloads"></a>
  <a href="https://www.npmjs.com/package/vite-plugin-vue-preview"><img src="https://img.shields.io/npm/v/vite-plugin-vue-preview" alt="Version"></a>
  <a href="https://www.npmjs.com/package/vite-plugin-vue-preview"><img src="https://img.shields.io/npm/l/vite-plugin-vue-preview" alt="License"></a>
</p>

<p align="center">
  <a href="./README.md">English</a>
</p>

一个为在 Markdown 中预览Vue组件而生的Vite插件，当然，也导出了一个 **VuePreview** 组件可以直接在 Vue 应用中使用

## 演示

<p align="center">
  <img src="./public/demo.gif" />
</p>

## 安装

```bash
pnpm add vite-plugin-vue-preview
```

## 特征

- 支持 Vue/Vitepress 应用
- 支持在线编辑

## 组件属性

### VuePreview

```ts
interface Props {
  // 初始化代码字符串
  code: string
  // 组件挂载时是否折叠代码
  collapse: boolean
  // 是否开启 ssr
  ssr: boolean
  // 预览部分背景颜色
  outputBgColor: string
}
```

## 用法

### Vue 应用

> 导入 VuePreview 组件及样式

```TS
import { createApp } from 'vue'
import { VuePreview } from 'vite-plugin-vue-preview'
import 'vite-plugin-vue-preview/dist/style.css'

const app = createApp({})

app.component('VuePreview', VuePreview)
```

### Vitepress 应用

> 导入 VuePreview 组件及样式，同时配置插件设置

```TS
// vite.config.ts
import { defineConfig } from 'vite'
import { VuePreviewPlugin } from 'vite-plugin-vue-preview'

export default defineConfig({
  plugins: [VuePreviewPlugin()],
})

// .vitepress/theme/index.ts
import DefaultTheme from 'vitepress/theme'
import { VuePreview } from 'vite-plugin-vue-preview'
import 'vite-plugin-vue-preview/dist/style.css'

export default {
  ...DefaultTheme,
  enhanceApp(ctx) {
    DefaultTheme.enhanceApp(ctx)
    ctx.app.component('VuePreview', VuePreview)
  },
}
```

一旦你按照上述流程配置完成，你就可以在你的markdown文件中使用了：

```md

\```vue preview
<template>
    <div>Demo: vite-plugin-vue-preview</div>
</template>
\```
```

## 声明

- 核心代码来源于 [@vue/repl](https://github.com/vuejs/repl)
