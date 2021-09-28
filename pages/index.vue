<template>
  <main>
    <banner :dynamic-data="dataHome.components[0]" />
    <the-resort :dynamic-data="dataHome.components[1]" />
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
      title: 'Home',
      script: [
        { src: '/luxy.min.js', body: true },
      ]
    }
  },
  mounted() {
  }
}
</script>
