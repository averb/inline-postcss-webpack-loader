# inline-postcss-webpack-loader

Inspired by the [inline-css-webpack-loader](https://github.com/AvraamMavridis/inline-css-webpack-loader). Use it if you need sass/scss preprocessing.

Convert `postcss`, `css` files to React friendly objects that you can use to inline styles to your components.

Includes `postcss-cssnext` and `postcss-nested`

## Install

[![NPM](https://nodei.co/npm/inline-postcss-webpack-loader.png?mini=true)](https://nodei.co/npm/inline-postcss-webpack-loader/)

Webpack config:

```js
{
  test: /\.css$/,
  loader: 'inline-postcss-webpack-loader'
},
```

## Example

CSS file:

```css
.button {
  color: var(--red);
  position: relative;
  font-size: var(--font16);
  line-height: 1.5;

  &:hover {
    opacity: 0.6;
  }

  & .icon {
    color: var(--white);
  }

  &:nth-child(2) {
    color: var(--blue);
  }
}
```

Convert to:

```js
button: {
  color: '#f00',
  position: 'relative',
  fontSize: '16px',
  lineHeight: '1.5',
};

button_hover: {
  opacity: '0.6',
};

button__icon: {
  color: '#fff',
};

button_nth_child_2: {
  color: '#00f';
}
```

Usage:
```js
import React from 'react';

import * as css from './styles.css';


export default const Button = () => (
  <button style={ css.button }>Submit</button>
)
```
