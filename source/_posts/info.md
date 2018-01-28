---
title: 小型企业内部接口调试项目
date: 2018-01-28 15:37:46
tags: system, api,前端接口对接,后端
---

#小型企业内部接口调试项目

## https://gitee.com/charsle/restApi.git  

### 如果觉得喜欢，欢迎star

#### 系统说明
  1. 系统分为后台开发人员接口上传，前端人员接口展示,统一进行登陆
![统一进行登陆](https://gitee.com/uploads/images/2018/0127/183539_8060b43e_447841.png "QQ20180127-180825@2x.png")

  2. 系统分为后台开发人员接口进行项目配置，可以对该项目进行增删改查，
![项目配置](https://gitee.com/uploads/images/2018/0127/183702_0040927f_447841.png "QQ20180127-182605@2x.png")

  3. 系统分为后台开发人员接口进行接口配置，对接口进行增删改查
![接口配置](https://gitee.com/uploads/images/2018/0127/183804_1566a606_447841.png "QQ20180127-182638@2x.png")

   4. 前端人员接口展示，进行接口的调试，以及需要授权的接口，进行设置
![前端人员调试](https://gitee.com/uploads/images/2018/0127/183952_ca09b3ce_447841.png "QQ20180127-182908@2x.png")


### Development

```bash
$ npm i
$ npm run dev
$ open http://localhost:7001/
```

### Deploy

```bash
$ npm start
$ npm stop
```

### npm scripts

- Use `npm run lint` to check code style.
- Use `npm test` to run unit test.
- Use `npm run autod` to auto detect dependencies upgrade, see [autod](https://www.npmjs.com/package/autod) for more detail.


[egg]: https://eggjs.org