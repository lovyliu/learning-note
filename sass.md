# sass 语法 #

### 1. 嵌套写法 ###
```css
.page{
    .content{
        .left-side{
            .profile{
                .name{
                    font-size: 2rem;
                }
                .age{
                    color: red;
                }
            }
        }
    }
}

/* SCSS 中还可以进行属性嵌套 */
.item-border {
    border: {
        style: solid;

        left: {
            width: 1px;
            color: red;
        }
        right: {
            width: 2px;
            color: blue;
        }
    }
}

/* SCSS 对父选择器的引用 */
.btn {
    color: #ccc;
    &:hover {
        color: red;
    }
    &:visited {
        color: blue;
    }
}
```

### 2. 把属性值定义成变量（可复用） ###
```css
@success-color: #ccc;
.success-bg{
  background: $success-color;
}

/* SCSS 可以使用+,-,*,/,%等数学操作符。并且如果变量是带单位的，例如px，也可以正确的进行运算 */
#navbar {
    $navbar-width: 800px;

    width: $navbar-width;
}

/* 使用#{}符号可以将变量查到属性名，或者选择器中 */
$side: top;
$radius: 10px;
.round-#{$side} {
    border-#{$side}-radius: $radius;
    -moz-border-#{$side}-radius: $radius;
    -webkit-border-#{$side}-radiux: $radius;
}
```

### 3. 文件引入 ###
```css
@import "common";
@import "popup";
...
```


### 4. mixin ###
```css
@mixin grey-border-radius{
    border: 1px solid #e3e3e3;
    border-radius: 2px;
}
.description{
    @include grey-border-radius;
    color: red;
}
.article{
    @include grey-border-radius;
    color: #444;
}

/* mixin 可以传参数，并且可以给参数设置默认值*/
@mixin round($side, $radius: 10px) {
    border-#{$side}-radius: $radius;
    -moz-border-#{$side}-radius: $radius;
    -webkit-border-#{$side}-radiux: $radius;
}

#navbar li {
    @include round(top);
}
#footer {
    @include round(top, 5px);
}
```

### 5. 继承 ###
```css
.base-nav {
    color: red;
}
.new-nav {
    @extend .base-nav;
    text-align: center;
}
```

### 6. 控制语句 ###
`@if` `@else`
```css
$navbar-width: 800px;
$item: 5;
p {
    @if $navbar-width/$item - 10px == 200 { border: 2px dotted; }

    @else { border: 1px solid; }
}
```
`@for`

```css
@for $i from 1 to 5 {
    .border-#{$i} {
        border: #{$i}px solid blue;
    }
}
```

`@while`
```css
$i: 1;
@while $i < 5 {
    .border-#{$i}{border: #{$i}px solid blue; }
    $i: $i + 1;
}
```

`@each`
```css
$i: 1;
@each $item in add, update, remove, share {
    .icon-#{$item} {
        background-image: url("/image/#{$item}.jpg");
    }
}
```

### 7. 自定义函数 ###
```CSS
@function double($n) {
    @return $n * 2;
}
#navbar {
    width: double(5px);
}
```


#### 参考链接 ####
* [sass 官网](http://sass-lang.com/)
* [前端CSS的工程化——掌握Sass这四大特性就够了](https://juejin.im/entry/5a44404a51882560b6529af0)
* [SASS用法介绍](http://www.imbeta.cn/sassyong-fa-jie-shao.html#sassyong-fa-jie-shao)
