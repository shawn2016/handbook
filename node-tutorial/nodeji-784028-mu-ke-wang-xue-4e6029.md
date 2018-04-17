## url.parse

一个URL字符串转换成对象并返回。

复制代码 代码如下:
url.parse(urlStr, [parseQueryString], [slashesDenoteHost])

接收参数：

urlStr url字符串

parseQueryString 为true时将使用查询模块分析查询字符串，默认为false

slashesDenoteHost

默认为false，//foo/bar 形式的字符串将被解释成 { pathname: ‘//foo/bar' }

如果设置成true，//foo/bar 形式的字符串将被解释成 { host: ‘foo', pathname: ‘/bar' }

例子：

```
var a = url.parse('http://example.com:8080/one?a=index&t=article&m=default');
console.log(a);
```

```
//输出结果：
{
protocol : 'http' ,
auth : null ,
host : 'example.com:8080' ,
port : '8080' ,
hostname : 'example.com' ,
hash : null ,
search : '?a=index&t=article&m=default', 
query : 'a=index&t=article&m=default',
pathname : '/one',
path : '/one?a=index&t=article&m=default',
href : 'http://example.com:8080/one?a=index&t=article&m=default'
}
```

Url.resolve

# querystring.stringify

## querystring.escape

