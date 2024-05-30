# unocss-preset-theme

This is a fork of [unocss-preset-theme](https://github.com/unpreset/unocss-preset-theme).

Just modify the following part:

- [fix: safelist] Media query style in safelist config。[unocss-preset-theme #69](https://github.com/unpreset/unocss-preset-theme/pull/69)

## Installation

```bash
npm i -D @wtto00/unocss-preset-theme
```

## Usages

Usually you just need to set your `light theme` to `unocss` and your `dark theme` to `presetTheme`. This preset will transform your provide theme into css variables, then you just need to set the `dark` class or `compact` class (Depends on your theme name) in your html and you're done.

Just like this

```typescript
import Unocss from 'unocss/vite';
import type { Theme } from 'unocss/preset-uno';
import { presetUno } from 'unocss';
import presetTheme from '@wtto00/unocss-preset-theme';
import type { Theme } from '@unocss/preset-uno';
import type { Preset } from 'unocss';

Unocss<Theme>({
  // Configure light themes
  theme: {},
  presets: [
    presetUno<Theme>(),
    presetTheme<Theme>({
      theme: {
        // Configure dark themes
        dark: {},
        // Configure compact themes
        compact: {},
      },
    }) as Preset<Theme>,
  ],
});
```

This will be the final generated css

```css
/* darkMode: class */
.dark {
}
:root {
}
.compact {
}

/* If you set darkMode to media, the css will look like this */
.compact {
}
@media (prefers-color-scheme: dark) {
}
@media (prefers-color-scheme: light) {
}
```

Then, you simply apply it as follows

```html
<div class="dark">
  Dark mode
  <div class="compact">
    <div class="px-md">Use compact theme</div>
  </div>
</div>
```

## Options

### prefix

The prefix of the generated css variables, default is `--un-preset-theme`

### theme

Your different theme. like `{ dark: {}, other: {} }`

### selectors

Customize the selectors of the generated css variables `{ light: ':root', [themeName]: '.[themeName]' }`

## Examples

- [playground](./examples/playground/)
- [media](./examples/media/)

## Contributors

<a href="https://github.com/unpreset/unocss-preset-theme/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=unpreset/unocss-preset-theme" />
</a>

## License

MIT License
