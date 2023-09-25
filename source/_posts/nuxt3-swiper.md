---
title: nuxt3 中使用最新版本 swiper
categories:
  - 技术
  - 前端
tags:
  - nuxt3
  - swiper
---

# 一、前言
公司实习生重构官网时使用了 nuxt3，但是在用 swiper 时却卡住了，找我帮忙看下，我原以为随便一搜，10 分钟内搞定，但是竟花了不少功夫，因为目前关于这类的文章要不太久，要不太乱，参考性不大，所以将最新解决方案记录下来。
# 二、目标
nuxt3 中使用最新版本的 swiper。
# 三、实现
```js
<template>
  <swiper
    :direction="'vertical'"
    :pagination="{
      clickable: true,
    }"
    :modules="modules"
  >
    <swiper-slide>Slide 1</swiper-slide>
    <swiper-slide>Slide 2</swiper-slide>
    <swiper-slide>Slide 3</swiper-slide>
    <swiper-slide>Slide 4</swiper-slide>
    <swiper-slide>Slide 5</swiper-slide>
    <swiper-slide>Slide 6</swiper-slide>
  </swiper>
</template>

<script>
  // 导入 Swiper、SwiperSlide 组件
  import { Swiper, SwiperSlide } from 'swiper/vue';
  // 导入 Swiper 基础样式
  import 'swiper/css';
  // 导入 Pagination 模块样式
  import 'swiper/css/pagination';
  // 导入 Pagination 模块
  import { Pagination } from 'swiper/modules';

  export default {
    components: {
      Swiper,
      SwiperSlide
    },
    setup() {
      return {
        modules: [Pagination]
      };
    }
  };
</script>

<style>
#__nuxt {
  height: 100%;
}

html,
body {
  position: relative;
  height: 100%;
}

body {
  background: #eee;
  font-family: Helvetica Neue, Helvetica, Arial, sans-serif;
  font-size: 14px;
  color: #000;
  margin: 0;
  padding: 0;
}

.swiper {
  width: 100%;
  height: 100%;
  /* width: 500px;
  height: 500px; */
  border: 1px solid red;
}
</style>
``` 
代码其实很简单，但有一点**需要注意，那就是 .swiper 的宽高要给对**。我一开始照着官方文档的例子写的时候，轮播是出来了，但是垂直轮播的效果没有，排查了才发现，例子里 .swiper 的宽高是百分比，它继承的是 #app 的宽高，但是我用的 nuxt3，里面没有 #app，只有 #__nuxt。

实现效果如下：
![nuxt-swiper.gif](./imgs/nuxt-swiper.gif)
# 四、个人收获
解决问题，还是优先看官方文档。当然，如果文档晦涩难懂，或者过长不方便查找时，对症进行谷歌搜索也是可以的，灵活搭配。
# 五、源码
[nuxt3-swiper](https://github.com/Rainst9/article-example/tree/main/nuxt3-swiper)
# 六、参考链接
1. [swiper](https://swiperjs.com/demos#vertical)
