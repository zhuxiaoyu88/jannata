<template>
  <main>
    <Banner :dynamic-data="dataHome.components[0]" />
  </main>
</template>

<script>
export default {
  async asyncData({ $axios, req, params, store }) {
    const dataHome = await $axios.$get('/data.json').then(res => res)

    return { dataHome }
  },
  data() {
    return {

    }
  },
  head() {
    return {
      title: 'Home'
    }
  }
}
</script>
