GET后退按钮/刷新无害，POST数据会被重新提交（浏览器应该告知用户数据会被重新提交）。

GET书签可收藏，POST为书签不可收藏。

GET能被缓存，POST不能缓存 。

GET编码类型application/x-www-form-url，POST编码类型encodedapplication/x-www-form-urlencoded 或 multipart/form-data。为二进制数据使用多重编码。

GET历史参数保留在浏览器历史中。POST参数不会保存在浏览器历史中。

GET对数据长度有限制，当发送数据时，GET 方法向 URL 添加数据；URL 的长度是受限制的（URL 的最大长度是 2048 个字符）。POST无限制。

GET只允许 ASCII 字符。POST没有限制。也允许二进制数据。

与 POST 相比，GET 的安全性较差，因为所发送的数据是 URL 的一部分。在发送密码或其他敏感信息时绝不要使用 GET ！POST 比 GET 更安全，因为参数不会被保存在浏览器历史或 web 服务器日志中。

GET的数据在 URL 中对所有人都是可见的。POST的数据不会显示在 URL 中。

