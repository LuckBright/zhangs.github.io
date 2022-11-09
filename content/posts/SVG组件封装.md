---
categories:
- 组件封装
date: '2022-11-09T06:13:00.000Z'
showToc: true
tags:
- 组件
title: SVG组件封装

---



### 关键插件安装

```javascript
yarn add vite-plugin-svg-icons -D
```

### 所有svg 文件都存放在固定的路径，我这里的路径为

```javascript
src/assets/svg
```

### vite.config.ts

```javascript
import { createSvgIconsPlugin } from 'vite-plugin-svg-icons'

export default defineconfig({
	plugin: [
		/** svg 文件导入 */
    createSvgIconsPlugin({
      // 指定要缓存的图标文件夹
      iconDirs: [resolve(process.cwd(), 'src/assets/svg')],
      // 执行icon name的格式
      symbolId: 'icon-[dir]-[name]'
    }),
	]
})
```

### main.ts

```javascript
import 'virtual:svg-icons-register'

import svgIcon from '@/components/svgicon/index.vue'

const app = createApp(App)
// 全局组件引入
app.component(svgIcon.name, svgIcon)
app.mount("#app")
```

### src/components/svgicon/index.vue

```javascript
<template>
  <svg :class="svgClass" v-bind="$attrs" :style="{ color: svgColor }">
    <use :xlink:href="iconName" /> 
  </svg>
</template>

<script lang="ts">
import { defineComponent, computed, toRefs } from "vue";

export default defineComponent({
  name: 'SvgIcon',
  props: {
    name: {
      type: String,
      required: true,
    },
    svgColor: {
      type: String,
      default: '',
    },
  },
  setup(props) {
    const { name } = toRefs(props)
    const iconName = computed(() => `#icon-${name.value}`); 
    const svgClass = computed(() => {
      if (name.value) {
        return `svg-icon icon-${props.name}`;
      }
      return 'svg-icon';
    });
    return {
      iconName,
      svgClass,
    };
  },
});
</script>

<style lang="scss">
.svg-icon {
  width: 1.6em;
  height: 1.6em;
  margin-left: 3px;
}
</style>
```



