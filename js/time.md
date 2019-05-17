# 时间戳

> 时间戳是指格林威治时间 1970 年 01 月 01 日 00 时 00 分 00 秒(**北京时间 1970 年 01 月 01 日 08 时 00 分 00 秒**)起至现在的总秒数。
>
> 如果推荐 [Moment.js - JavaScript 日期处理类库](http://momentjs.cn/)

## JavaScript 获取当前时间戳

方法一：

```js
var timestamp = Date.parse(new Date());
```

方法二：

```js
var timestamp = new Date().valueOf();
```

方法三：

```js
var timestamp = new Date().getTime();
```

第一种获取的时间戳是精确到秒，第二种和第三种是获取的时间戳精确到毫秒。

## 日期转化为时间戳

```js
/**
 * 将正常时间格式转化为时间戳
 * @param {String} time [正常时间格式，如：2019-04-01 13:10:10]
 */
function transToTimestamp(time = null) {
  // 没有对 time 做合法性校验
  // 假设传入的 time 都是合法的时间格式：2019-04-01 13:10:10
  const date = new Date(time);
  const timestamp = date.getTime(); // 13 位数字，精确到毫秒
  return timestamp;
}
```

## 时间戳转化为日期

```js
function add0(m){return m<10?'0'+m:m }

function dateFormat (timestamp, formats) {
  formats = formats || 'Y-m-d';
  var date = timestamp ? new Date(timestamp) : new Date();
  var obj = {
    YYYY: add0(date.getFullYear()),
    MM: add0(date.getMonth() + 1),
    DD: add0(date.getDate()),
    hh: add0(date.getHours()),
    mm: add0(date.getMinutes()),
    ss: add0(date.getSeconds()),
  }
  return formats.replace(/YYYY|MM|DD|hh|mm|ss/ig, function (matches) {
    return obj[matches];
  });
}
```
