<template>
  <nuxt-link :to="{path: `/news/${item.id}`}">
    <li>
      <h2>{{ item.title }}</h2>
      <p>{{ item.content }}</p>
    </li>
  </nuxt-link>
</template>

<script>
export default {
  name: "NewsItem",

  props: ['item']
}
</script>

<style scoped>

</style>
