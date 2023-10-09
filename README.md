# Astro 中间件，解决中文 md 乱码问题

## Bug 描述

在 Astro v3 中，在 `pages` 下创建 `test.md` 文件，生成 `/test` 的页面路由，`astro dev` 开发服务器下会导致中文乱码。

`astro build` 后，中文正常。

## Bug 原因

产生此 Bug 的原因是 Astro v3 中未设置 `Content-Type`，导致浏览器无法正确解析中文。

请查看相关 issue：[Astro v3 markdown page router Chinese get unreadable characters](https://github.com/withastro/astro/issues/8676)

## 解决方案

- 使用 [Layout](https://docs.astro.build/zh-cn/core-concepts/layouts/#markdownmdx-布局)，在 Layout 中设置 `<meta charset="utf-8" />`
- 使用 [Content Collections](https://docs.astro.build/zh-cn/guides/content-collections/)
- 使用此中间件

## 使用方法

```ts
import { defineMiddleware } from "astro:middleware";

export const onRequest = defineMiddleware(async (context, next) => {
    const response = await next();
    response.headers.set('Content-Type', 'text/html; charset=utf-8');

    return response;
});
```
请在 examples 文件夹查看 [示例](https://github.com/liruifengv/astro-middleware-cn/tree/main/examples)

关于中间件的更多信息，请查看 [Astro 中间件文档](https://docs.astro.build/zh-cn/guides/middleware/)

## License

本项目使用 [MIT License](./LICENSE)