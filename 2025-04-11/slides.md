---
title: ExCaller
info: 一个简约风格的随机点名工具
mdc: true
---

<h1 flex justify-self-center items-center>
  <img src="./assets/logo.avif" size-16>
  <span>ExCaller</span>
</h1>

一个简约风格的随机点名工具{.text-center}

<!--
在开始之前：

- 打开 [Mixpanel](https://mixpanel.com/p/2NXuZUnZ4wcGKhQEJ1aAHj) 备用，避免等待加载
- 打开 [#64 的预览网址](https://deploy-preview-64--ex-caller.netlify.app/) 备用

***

ExCaller 是一个简约风格的随机点名工具。

它的基本信息，创作说明中已详细介绍过。

我今天既然站在这里，就讲讲别的，代码之外的事情。
-->

---

# 为什么要做 ExCaller

- 课堂中常有随机点人的需求
- 老师接到新班级后，只能低头看着名单点人
- 公平性问题
- ![](./assets/classnamepicker.avif){.w-80}

<!-- 讲完四点后马上切到下一页 -->

---
class: flex flex-col justify-center items-center
---

<div class="spin" />

<style scoped>
.spin {
  width: 150px;
  height: 150px;
  background: url("./assets/loading.avif") left / auto 100% no-repeat;
  animation: loading 1.5s steps(1, start) 0s 1 normal none;
}

@keyframes loading {
  from { background-position: 0 0; }
  2.8% { background-position: -150px 0; }
  5.6% { background-position: -300px 0; }
  8.3% { background-position: -450px 0; }
  11.1% { background-position: -600px 0; }
  13.9% { background-position: -750px 0; }
  16.7% { background-position: -900px 0 }
  19.4% { background-position: -1050px 0; }
  22.2% { background-position: -1200px 0; }
  25% { background-position: -1350px 0; }
  27.8% { background-position: -1500px 0; }
  30.6% { background-position: -1650px 0; }
  33.3% { background-position: -1800px 0; }
  36.1% { background-position: -1950px 0; }
  38.9% { background-position: -2100px 0; }
  41.7% { background-position: -2250px 0; }
  44.4% { background-position: -2400px 0; }
  47.2% { background-position: -2550px 0; }
  50% { background-position: -2700px 0; }
  52.8% { background-position: -2850px 0; }
  55.6% { background-position: -3000px 0; }
  58.3% { background-position: -3150px 0; }
  61.1% { background-position: -3300px 0; }
  63.9% { background-position: -3450px 0; }
  66.7% { background-position: -3600px 0; }
  69.4% { background-position: -3750px 0; }
  72.2% { background-position: -3900px 0; }
  75% { background-position: -4050px 0; }
  77.8% { background-position: -4200px 0; }
  80.6% { background-position: -4350px 0; }
  83.3% { background-position: -4500px 0; }
  86.1% { background-position: -4650px 0; }
  88.9% { background-position: -4800px 0; }
  91.7% { background-position: -4950px 0; }
  94.4% { background-position: -5100px 0; }
  97.2% { background-position: -5250px 0; }
  to { background-position: 0 0; }
}
</style>

<!-- 这一页等讲完“因此，我开发了 ExCaller”就过 -->

---
class: flex flex-col justify-center text-center
---

# 颜值是第一生产力{.text-6xl! mb-4}

<p text-2xl>
  ——
  <img src="./assets/lark.svg" inline size-12>飞书未来无限大会
</p>

<!--
不知道各位有没有听说过这一话：“颜值是第一生产力”。

几年前的我比较闲，有时间看各种 conference，在飞书的一次发布会直播上听到了这句话，这和我的想法刚好契合。

如果一个产品的颜值不高，就相当于一条街上堆满了垃圾污水，人们远远地看到就会绕开。

反之，如果产品的颜值高，就像街旁开满了樱花，人们大多优先选择走这条路。

然而，优先选择的前提绕的路不远。

如果一个产品追求颜值，却把功能藏得太深，甚至搞捆绑销售、全家桶，那就是本末倒置。

因此，ExCaller 的设计原则是“简洁，但不简单”。
-->

---
class: flex flex-col justify-center items-center
---

# 简洁，但不简单

<script lang="ts" setup>
import s1 from './assets/screenshots/welcome.avif?url';
import s2 from './assets/screenshots/setting.avif?url';
import s3 from './assets/screenshots/namelist.avif?url';
import s4 from './assets/screenshots/namelist/batch-input.avif?url';
import s5 from './assets/screenshots/namelist/import-excel.avif?url';
import s6 from './assets/screenshots/theme.avif?url';
import s7 from './assets/screenshots/plan.avif?url';

const showcases = [s1, s2, s3, s4, s5, s6, s7];
</script>

<img v-for="item in showcases" v-after v-click.hide :src="item" h-100>

<style scoped>
.slidev-layout h1 + p {
  opacity: 1;
}

.slidev-vclick-target:not(.slidev-vclick-current),
.slidev-vclick-current:has(+ .slidev-vclick-current) {
  display: none;
}
</style>

<!--
【逐个解释每张截图的功能】

（别忘了 showcase #5 之后还有个导出功能，没有截图但要讲）。
-->

---

# 跟随最佳实践

- 单元测试
- 类型检查
- 代码风格规范与自动修复
- 依赖更新与供应链漏洞通知
- 一次修改，一次部署
- PR 预览

以及我主观上的：

- Bun 而不是 Node.js
- ESLint 而不是 ESLint+Prettier
- Tauri 而不是 Electron

<v-click>

![](./assets/qr/stats.svg){.size-54 .float-right .mr-8 .mt-[-8rem]}

分组功能：[typed-sigterm/ex-caller#64](https://github.com/typed-sigterm/ex-caller/pull/64)

预览地址：https://deploy-preview-64--ex-caller.netlify.app

</v-click>

<!--
写过代码的人应该都有体验过，如果你在网上搜一个问题，比如“ESLint Unexpected token 错误怎么解决”，
那你得到的解法，尤其是来自 CSDN 的，大多数是把 ESLint 关掉了。

一年前，ESLint 发布了 v9，带来了全新的配置系统 Flat Config。
而你上网搜，99% 的文章还是用旧的配置系统 `.eslintrc`。

中文 IT 平台上许多人都缺乏对新技术的关注度，甚至对新技术有排斥的情绪。
而我不妥协，毕竟我又不赶工期，我还要追求代码健壮性和开发者体验。

所以我跟随最佳实践。

【逐条解释】

有人问：“你做了这么多，除了你自己在开发时的体验以外，最终有没有产生价值呢？”

ExCaller 不是商业产品，有真实用户就是有价值。

【下一页】
-->

---

# 真有用户吗

从 ExCaller 发布至今，我还没有做过任何推广，仅靠**自然流量**获得用户

然而，在不推广策略下，ExCaller 不仅有真实用户，而且出现了高质量的用户反馈：

<v-click>

> 作者您好：
>
> 我是一名老师，偶然间找到您的软件。我和我的同事非常喜欢您的作品，使用过程中遇到一些麻烦：
>
> 我们需要在多个班不同的电脑上用，但是电脑上安装了恢复系统，所以每次使用都要重新安装一遍，重新导入各个班的名单。不知道作者是否有时间制作一版可以放到 U 盘里直接使用的版本，一次设置即可在每台电脑上使用。
>
> 冒昧打搅，谢谢！

<p class="text-right">
  ——
  <a href="https://github.com/typed-sigterm/ex-caller/issues/51">
    typed-sigterm/ex-caller#51
  </a>
</p>

这个 issue 于 2025/2/21 创建，我当天回复了临时解决方案。

一周后，我发布了 ExCaller v1.1.0，添加了**便携版**，无需安装即可使用。

</v-click>

<!--
ExCaller 的开发和反馈过程是在 GitHub 上完全透明的，这在某种程度上也是对用户的一种承诺。

那么高质量反馈毕竟是个例吧，有了质，有没有量呢？
-->

---

# 数据胜于雄辩

用户行为分析是每个产品都应有的部分

从 v1.1.1 起，我在 ExCaller 中添加了用户行为统计功能。

默认情况下，用户**打开应用**、**开始点名**、**确认和取消更新**行为会匿名上报到数据分析平台 Mixpanel。

完整的报告可以在此查看：https://mixpanel.com/p/2NXuZUnZ4wcGKhQEJ1aAHj

![](./assets/qr/stats.svg){.size-54 .float-right .mr-8}

<!--
关于量，自然要用数据说话。

【读稿】

我认为，在仅靠搜索和口口相传的情况下，对于 ExCaller 这样一个小工具来说，这是一个不错的数据。

当然，不推广策略实际上是对学业压力的妥协，也不算什么光彩的事。中考后，我还是会考虑补上推广这一块。
-->

---

# 站在巨人的肩膀上

开源造就了当今的世界，ExCaller 也不例外

<div class="[&>*]:size-12" flex flex-wrap gap-8 mt-24>
  <LogosTypescriptIcon />
  <LogosRust />
  <LogosBun />
  <LogosNuxtIcon opacity-0 />
  <LogosVue />
  <LogosVitejs />
  <LogosVitest />
  <LogosUnocss />
  <LogosPinia />
  <LogosMixpanel w-16 />
  <LogosTauri />
  <LogosPostcss />
  <LogosNaiveui />
  <LogosZod />
  <LogosVueuse />
  <LogosUnjs />
  <LineMdIconify2StaticTwotone />
  <SimpleIconsLucide />
  <LogosEslint />
  <LogosRenovatebot />
  <LogosNetlifyIcon />
  <LogosGithubActions />
  <LogosSlidev v-click transition-opacity duration-300 />
</div>

<PoweredBySlidev v-click="'+0'" float-right mt-24 transition-opacity duration-300 />

<!--
ExCaller 作为现代软件，背后一定有一条庞大的供应链。

根据不完全统计，ExCaller 共直接或间接依赖了 565 个库。

诶这里怎么有个空格？这个我们待会再说。

以上是部分直接依赖的库。

除此之外呢，在屏幕上播放的这个，实际上不是 PPT，【点击】而是用 Slidev 制作的网页。
Slidev 是专为开发者打造的演示文稿工具，在这里不多解释了。
-->

---

# 开源！

ExCaller 以 MIT 许可证开源，虽然现在只有我一个贡献者

<div v-click mt-8>

## 我的开源历程

![](./assets/heat-map-wtf.avif){.w-40 .float-right .mr-8}

2022 — 34 次贡献

2023 — 778 次贡献（部分数据缺失）

2024 — 920 次贡献

2025 — 322 次贡献（截至 2025/4/10）

共贡献给 115+90=204 个仓库（截至 2025/4/10）

</div>

<v-click>我认为，开源更多地是一种态度，表达的是对他人劳动成果的尊重和对社区的回馈。</v-click>

<!--
我因此还被同学评价为“卷”。

我庆幸我出生在开放源代码和自由软件运动繁荣发展的时代。
-->

---

# 轮子的选择

<div flex gap-12 text-xl justify-self-center mt-24>
  <LogosVue size-24 />
  <LogosTauri size-24 />
</div>

<div flex flex-col items-center justify-self-center mt-4>
  <LogosNuxtIcon v-click.hide flex size-24 transition-opacity duration-500 />
  <a v-click="'+0'" class="mt-[-4rem]" href="https://github.com/typed-sigterm/ex-caller/pull/60" block text-2xl transition-opacity duration-500 delay-300>
    typed-sigterm/ex-caller#60
  </a>
</div>

<!--
ExCaller 的架构由三大块组成：

- 负责前端的 Vue
- 负责打包成原生应用的 Tauri
- “元框架”Nuxt

Nuxt 处理了包括路由、状态管理、自动导入等一系列事情，减少了 Vue“过于灵活”的问题，当然也付出了一定的成本。

不得不说，Nuxt 确实是个好轮子，它最终加给用户的成本是非常低的。我在最近两年的开源生涯中，几乎所有的项目都用 Nuxt。

但是，我的电脑难以承受 Nuxt 在开发时的成本。
我打开项目，等 VS Code 把 Nuxt 生成的类型信息加载完，一分钟过去了。
启动一下开发服务器，又一分钟过去了。
重命名一个函数，又一分钟过去了。
几分钟看似短，但是十分难熬的，而且一条要经历多次这样的等待。

在权衡利弊后，我感到在技术选型时出现了偏差。于是，我在一周前决定放下 Nuxt，改用纯血 Vue。

前面那一页中的空格，就是 Nuxt，它是个好轮子，但不适合这个的项目。
-->

---

# 未来计划

中考还剩 70 天

维护者招募：[typed-sigterm/ex-caller#56](https://github.com/typed-sigterm/ex-caller/discussions/56)

Roadmap: https://github.com/users/typed-sigterm/projects/5/views/1

<!--
中考在即，我要再次向学业妥协。

我开始在智教联盟论坛之类的地方寻找更广泛的社区参与，希望 ExCaller 能够成为社区驱动的项目。
-->
