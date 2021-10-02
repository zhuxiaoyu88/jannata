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
      <the-resort :dynamic-data="dataHome.components[1]" data-scroll-section />
      <the-stay :dynamic-data="dataHome.components[2]" data-scroll-section />
      <dinner :dynamic-data="dataHome.components[3]" data-scroll-section />
      <relaxing :dynamic-data="dataHome.components[4]" data-scroll-section />
      <testimoni :dynamic-data="dataHome.components[5]" data-scroll-section />
    </main>
  </LocomotiveScroll>
</template>

<script>
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
gsap.registerPlugin(ScrollTrigger)

export default {
  async asyncData({ $axios, req, params, store }) {
    const dataHome = await $axios.$get('/data.json').then(res => res)

    return { dataHome }
  },
  head() {
    return {
      title: 'Home'
    }
  },
  mounted() {
    this.initScrolltrigger()
    
    this.$nextTick(() => {
      const elementImage = document.querySelectorAll('[data-scroll-trigger-img]')
      elementImage.forEach((element) => this.imageAnimation(element))

      const elementText = document.querySelectorAll('[data-scroll-trigger-text]')
      elementText.forEach((element) => this.textAnimation(element))
    })
  },
  methods: {
    initScrolltrigger() {
      const locomotive = this.$refs.scroller.locomotive
      locomotive.on('scroll', ScrollTrigger.update)
      ScrollTrigger.scrollerProxy(locomotive.el, {
        scrollTop(value) {
          return arguments.length
            ? locomotive.scrollTo(value, 0, 0)
            : locomotive.scroll.instance.scroll.y
        },
        getBoundingClientRect() {
          return {
            top: 0,
            left: 0,
            width: window.innerWidth,
            height: window.innerHeight,
          }
        },
      })
    },
    imageAnimation(element) {
      gsap.from(element, {
        scrollTrigger: {
          trigger: element,
          scroller: this.$refs.scroller.locomotive.el,
          scrub: true,
          start: 'top center+=200',
          end: 'bottom center',
        },
        width: 0,
        ease: "power2.out",
        duration: 5,
        delay: .5
      })
    },
    textAnimation(element) {
      gsap.from(element, {
        scrollTrigger: {
          trigger: element,
          scroller: this.$refs.scroller.locomotive.el,
          scrub: true,
          start: 'top center+=200',
          end: 'bottom center',
          markers: true,
        },
        x: -25,
        opacity: .0,
        ease: "back",
        duration: 5,
        delay: .5
      })
    },
  }
}
</script>
