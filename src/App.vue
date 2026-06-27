<script setup>
const contacts = [
  { url: 'https://github.com/cioyu', sub: 'github主页' },
  { url: 'https://space.bilibili.com/1928417915', sub: 'B站主页' },
  { url: 'https://www.youtube.com/channel/UC_WmZj9i7MZV899g1iunwdA', sub: 'YouTube主页' },
  { url: 'mailto:cioyu32@gmail.com', sub: '电子邮箱' },
  { url: 'https://steamcommunity.com/profiles/76561199760499467/', sub: 'Steam主页' },
  { url: 'https://v.douyin.com/NiMz02B5XNI/', sub: '抖音主页' },
]
</script>

<template>
  <h1>Cioyu 的个人博客</h1>
  <img src="/favicon.ico" alt="头像">
  <p>网络专业学生.AI编程糕手.喜欢看小说.偶尔看下番,玩玩游戏. </p>
  <h2>联系方式</h2>
  <div>
    <a v-for="c in contacts" :key="c.sub" :href="c.url" target="_blank">
      <span v-if="c.sub" class="contact-sub">{{ c.sub }}</span><br>
    </a>
  </div>

  <footer>
    <div>
      <p>&copy; 2026 Cioyu </p>
    </div>
  </footer>
</template>


<style scoped>

</style>
