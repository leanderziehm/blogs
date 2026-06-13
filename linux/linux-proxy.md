# Linux Proxy

## APT proxy

<pre><code><strong>sudo vim /etc/apt/apt.conf.d01proxy
</strong></code></pre>

```
Acquire::http::Proxy
"http://192.168.0.101:8888";
```



## TinyProxy

[https://github.com/tinyproxy/tinyproxy](https://github.com/tinyproxy/tinyproxy)



## Squid Proxy

[https://github.com/squid-cache/squid](https://github.com/squid-cache/squid)
