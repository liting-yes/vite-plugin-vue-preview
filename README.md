<h1 align="center">vite-plugin-vue-preview</h1>

<p align="center">
  <a href="https://www.npmjs.com/package/vite-plugin-vue-preview"><img src="https://img.shields.io/npm/dm/vite-plugin-vue-preview" alt="Downloads"></a>
  <a href="https://www.npmjs.com/package/vite-plugin-vue-preview"><img src="https://img.shields.io/npm/v/vite-plugin-vue-preview" alt="Version"></a>
  <a href="https://www.npmjs.com/package/vite-plugin-vue-preview"><img src="https://img.shields.io/npm/l/vite-plugin-vue-preview" alt="License"></a>
</p>

<p align="center">
  <a href="./README.zh-CN.md">简体中文</a>
</p>

a vite plugin for code preview of vue component in markdown, of course, a **VuePreview** component is also exported for direct use in vue app.

## Demo

<p align="center">
  <img src="./public/demo.gif" />
</p>

## Install

```bash
pnpm add vite-plugin-vue-preview
```

## Features

- Support for Vue/Vitepress applications
- Support online editing

## Props

### VuePreview

```ts
interface Props {
  // Initialization code string
  code: string
  // Whether to collapse the code when the component is mounted
  collapse: boolean
  // Whether to turn on ssr
  ssr: boolean
  // Background color of preview part
  outputBgColor: string
}
```

## Usage

### Vue

> Import the VuePreview component and style

```TS
import { createApp } from 'vue'
import { VuePreview } from 'vite-plugin-vue-preview'
import 'vite-plugin-vue-preview/dist/style.css'

const app = createApp({})

app.component('VuePreview', VuePreview)
```

### Vitepress

> Import the VuePreview component / style and plugin

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

Once you've set up the above, you're ready to use it in your markdown file:

```md

\```vue preview
<template>
    <div>Demo: vite-plugin-vue-preview</div>
</template>
\```
```

## Statement

- Core code from [@vue/repl](https://github.com/vuejs/repl)
