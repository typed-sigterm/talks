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
-->

---

# 为什么要做 ExCaller

- 课堂中常有随机点人的需求
- 老师接到新班级后，只能低头看着名单点人
- 公平性问题
- ![](./assets/classnamepicker.avif){.w-80}

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

---
class: flex flex-col justify-center text-center
---

# 颜值是第一生产力{.text-6xl! mb-4}

<p text-2xl>
  ——
  <img src="./assets/lark.svg" inline size-12>飞书未来无限大会
</p>

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
别忘了 showcase #5 之后还有个导出功能，没有截图但要讲
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

---

# 数据胜于雄辩

用户行为分析是每个产品都应有的部分

从 v1.1.1 起，我在 ExCaller 中添加了用户行为统计功能。

默认情况下，用户**打开应用**、**开始点名**、**确认和取消更新**行为会匿名上报到数据分析平台 Mixpanel。

完整的报告可以在此查看：https://mixpanel.com/p/2NXuZUnZ4wcGKhQEJ1aAHj
，或扫描下方二维码：

![](./assets/qr/stats.svg){.size-54 .float-right .mr-8}

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

---

# 开源！

ExCaller 以 MIT 许可证开源，虽然现在只有我一个贡献者

<div v-click mt-8>

## 我的开源历程

![](./assets/heat-map-wtf.avif){.w-40 .float-right .mr-8}

2022 — 34 次贡献

2023 — 778 次贡献（部分数据缺失）

2024 — 920 次贡献

2025 — 308 次贡献（截至 2025/4/8）

共贡献给 115+89=204 个仓库（截至 2025/4/8）

</div>

<v-click>我认为，开源更多地是一种态度，表达的是对他人劳动成果的尊重和对社区的回馈。</v-click>

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

---

# 未来计划

中考还剩 70 天

维护者招募：[typed-sigterm/ex-caller#56](https://github.com/typed-sigterm/ex-caller/discussions/56)

Roadmap: https://github.com/users/typed-sigterm/projects/5/views/1
