# 封装 ajax

为了方便使用，按照 jquery.ajax 的接口来封装原生 ajax：

```js
function sendAjax (config) {
  var request = new XMLHttpRequest(); // 新建XMLHttpRequest对象
  request.onreadystatechange = function () { // 状态发生变化时，函数被回调
    if (request.readyState === 4) { // 成功完成
      // 判断响应结果:
      if (request.status === 200) {
        // 成功，通过responseText拿到响应的文本:
        config.success(JSON.parse(request.response));
      } else {
        // 失败，根据响应码判断失败原因:
        config.error(JSON.parse(request.response));
      }
    } else {
      // HTTP请求还在继续...
    }
  }
  request.open(config.type, config.url);

  for (key in config.headers) {
    request.setRequestHeader(key, config.headers[key])
  }

  if (config.type === 'POST') {
    // payload request
    request.send(JSON.stringify(config.data));
  } else {
    request.send(null);
  }

}
```


调用方法

```js
sendAjax({
  url: 'xxxxxx',
  type: 'POST',
  data: { name: 'zwc', age: 18 },
  headers: {
    "Content-Type": 'application/json',
    "tokenId":      'aaaaaa',
  },
  success: function (resp) {
    console.log('ok')
  },
  error: function (err) {
    console.log('fail')
  }
})
```