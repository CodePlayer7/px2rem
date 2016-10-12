# px2rem
[![npm version](https://badge.fury.io/js/webpack-px-to-rem.svg)](https://badge.fury.io/js/webpack-px-to-rem)

a webpack loader for converting `px` to `rem` when developing repsonsive webpage

## Table of Contents
  - [Introduction](#introduction)
  - [Installation](#installation)
  - [Usage](#usage)

## Introduction
this is your css or js declaration in `px`:
```css
//css
div {
  font-size:14px,
  width:100px
}
```
```javascript
//js such as in react
<Page style={{fontSize:'14px',width:'100px'}}/>
```
after converting based on `1rem=10px`
```css
//css
div {
  font-size:1.400rem,
  width:10rem
}
```
```javascript
//js such as in react
<Page style={{fontSize:'1.400rem',width:'10rem'}}/>
```
## Installation
```javascript
npm install webpack-px-to-rem --save-dev
```
## Usage
```javascript
//in your webpack.config.js

module.exports={
   ...
    module:{
        loaders:[
            {
                test:/\.jsx$/,
                loader:'webpack-px-to-rem',
                //the query is optional
                 query:{
                    // 1rem=npx default 10
                    basePx:10,
                    //only convert px greater than the given value default 0
                    //For the reason that tiny rem may be smaller than 1px and disappeare in tiny device
                    min:1,
                    //the rem value only has specific decimal places default 3
                    floatWidth:3
                }
                
            }
        ]
    }
    ...
  }
```
