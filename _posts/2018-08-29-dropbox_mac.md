#Mac os 下的 Dropbox 代理设置

Dropbox 设置 socks5 代理，服务器及端口可在文件`/Users/User_name/.ShadowsocksX-NG/gfwlist.js`中看到： 

```
var proxy = "SOCKS5 127.0.0.1:1086; SOCKS 127.0.0.1:1086; DIRECT;";
```

然后将服务器设置为`127.0.0.1`，端口设置为`1086`即可。