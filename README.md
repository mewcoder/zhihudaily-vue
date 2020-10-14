# 知乎日报接口跨域访问

使用request库做代理

```
npm i request -D
```

创建proxy.js，执行`node proxy.js`

核心是在返回的头部添加一项：
```
 // 设置所有域允许跨域
 res.setHeader('Access-Control-Allow-Origin', '*');
```