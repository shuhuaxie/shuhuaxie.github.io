---
layout: post
title:  "2017-3-29-android tips"
date:   2017-3-29 12:11:30 +0800

---
* android加载cookie
```java
        CookieManager cookieManager = CookieManager.getInstance();
        cookieManager.setAcceptCookie(true);
        StringBuilder sbCookie = new StringBuilder();
        cookieManager.removeSessionCookie();
        sbCookie.append(String.format("U=%s", UserManager.getIns().getUser().getSessionToken()));
        sbCookie.append(String.format(";domain=%s", ".chongdingdahui.com"));//domain必须要.开头 不然加载不进去
        cookieManager.setCookie(url, sbCookie.toString());
        if (android.os.Build.VERSION.SDK_INT >= android.os.Build.VERSION_CODES.LOLLIPOP) {
            cookieManager.flush();
        } else {
            CookieSyncManager.createInstance(this.getApplicationContext());
            CookieSyncManager.getInstance().sync();
        }
        // 这里可以cookieManager.getCookie(url)判断是否加载成功
```
* webView缓存
1.普通(LOAD_NORMAL 默认) 每次请求html css js,并且会返回304,速度比较快;
2.LOAD_NO_CACHE 每次都请求html css js,并且返回200
3.LOAD_CACHE_ELSE_NETWORK 每次都不请求html css js等静态资源,只请求普通get等


状态码:
HTTP/1.1 204 No Content

服务端缓存策略.
cache-control: max-age=30
expires: 10

客户端normal下:
没有过期 则不发起 html 等资源文件请求
过期则 发起资源文件请求,然后返回304.


