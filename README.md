# px2rem
[![npm version](https://badge.fury.io/js/webpack-px-to-rem.svg)](https://badge.fury.io/js/webpack-px-to-rem)

开发响应式网页，尤其是手机端，常常采取rem单位。这个webpack的小loader主要是省去了每次输入长、宽、字体等都要把像素px换算成rem的麻烦，
开发时直接输入px,最后打包打包时换算为rem。

[English Doc](https://github.com/CallMeXYZ/px2rem/blob/master/README-en.md)

## 内容列表
  - [介绍](#介绍)
  - [安装](#安装)
  - [使用](#使用)

## 介绍
这是你原先的css或者js代码
```css
// css
div {
    font-size: 14px;
    width: 100px;
}
```
```javascript
// js 例如 react
<Page style={{ fontSize: '14px', width: '100px' }} />
```
采取默认的 `1rem=10px` 转化后变成
```css
// css
div {
    font-size: 1.400rem;
    width: 10rem;
}
```
```javascript
// js such as in react
<Page style={{ fontSize: '1.400rem', width: '10rem' }} />
```

## 安装
```javascript
npm install webpack-px-to-rem --save-dev
```

## 使用
```javascript
//in your webpack.config.js

module.exports={
   ...
    module:{
        // 或者 loaders
        rules:[
            {
                test:/\.jsx$/,
                loader:'webpack-px-to-rem',
                // 这个配置是可选的
                 query:{
                    // 1rem=npx 默认为 10
                    basePx:10,
                    // 只会转换大于min的px 默认为0
                    // 因为很小的px（比如border的1px）转换为rem后在很小的设备上结果会小于1px，有的设备就会不显示
                    min:1,
                    // 转换后的rem值保留的小数点后位数 默认为3
                    floatWidth:3
                }

            }
        ]
    }
  }
```
