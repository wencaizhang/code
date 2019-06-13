# 被阻止的新窗口

## 常规的写法是

1. a 链接中使用 `target="_blank"` 属性

<open-new-window-link />

```html
<a href="https://baidu.com" target="_blank">新窗口打开百度</a>
```

2. 使用 window.open 

<open-new-window-button />

```js
window.open('https://baidu.com');
```

## 意外发生了

<open-new-window-async />

```js
setTimeout(function () {
  window.open('https://baidu.com');
}, 1000)
```