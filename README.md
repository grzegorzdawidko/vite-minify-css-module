# 📦 vite-minify-css-module

[![NPM version](https://img.shields.io/npm/v/vite-minify-css-module?color=a1b858&label=)](https://www.npmjs.com/package/vite-minify-css-module)

#### 🌈 Features

- 🍰 Minify css module class name
- 🍰 Support clean-css options

## 📦 Installation

```bash
npm i vite-minify-css-module@latest -D
```

#### support vite and rollup.

<details>
<summary>Basic</summary><br>

```ts
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';
import MinifyCssModule from 'vite-minify-css-module/vite';

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [
    react(),
    MinifyCssModule({
      cleanCSS: {
        level: {
          2: {
            mergeSemantically: true,
            restructureRules: true,
          },
        },
      },
    }),
  ],
});
```

<br></details>

## 🌸 DefaultConfiguration

```typescript
export interface PluginOptions {
  dictionary?: string;
  clearnCSS?: OptionsOutput;
}
```

## How does it work?

By default, when using css modules, you end up with hashes or other long class-names in your bundled css files:

```css
@keyframes _close-card_pzatx_1 {
  /* CSS HERE */
}

._card_pzatx_32 {
  /* CSS HERE */
}

._back_pzatx_49 ._content_pzatx_70 ._close_pzatx_74 {
  /* CSS HERE */
}
```

By using this module, the smalles possible classname will be used for each "id":

```css
@keyframes a {
  /* CSS HERE */
}

.v {
  /* CSS HERE */
}

.c .s .w {
  /* CSS HERE */
}
```
