<template>
  <LocomotiveScroll
      ref="scroller"
      :getted-options="{
        smooth: true,
        direction: 'vertical',
        smartphone: {
          smooth: true,
          direction: 'vertical',
        },
        tablet: {
          smooth: true,
          direction: 'vertical',
        },
      }"
    >
    <main>
      <banner :dynamic-data="dataHome.components[0]" data-scroll-section />
      <!-- <the-resort :dynamic-data="dataHome.components[1]" /> -->
      <div class="section-big-padding"></div>
      <relaxing :dynamic-data="dataHome.components[4]" data-scroll-section />
      <testimoni :dynamic-data="dataHome.components[5]" data-scroll-section />
    </main>
  </LocomotiveScroll>
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
  },
  mounted() {
  }
}
</script>
