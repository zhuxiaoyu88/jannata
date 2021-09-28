<template>
    <section class="banner">
        <flickity ref="flickity" :options="flickityOptions">
            <div v-for="item,id in sliderItem" :key="id" class="carousel-cell">
                <picture class="banner__container">
                    <source media="(min-width:768px)" :srcset="`${item.featured.aws_file_url}/${item.featured.path}/${item.featured.filename.big}`">
                    <source media="(max-width:767px)" :srcset="`${item.featured.aws_file_url}/${item.featured.path}/${item.featured.filename.medium}`">
                    <img :src="`${item.featured.aws_file_url}/${item.featured.path}/${item.featured.filename.big}`" :alt="item.description" class="banner__image">>
                </picture>
                <article class="banner__content">
                    <h2 class="banner__title" v-html="item.title"></h2>
                    <p class="banner__description">{{ item.description }}</p>
                    <a :href="item.link.url" class="banner__content-link">{{ item.link.title }}</a>
                </article>
            </div>
        </flickity>
    </section>
</template>

<script>
import Flickity from 'vue-flickity'
export default {
    components: {
        Flickity
    },
    props: {
        dynamicData: {
            type: Object,
            default() {
                return {
                    message: 'Unavailable data'
                }
            }
        }
    },
    data() {
        return {
            flickityOptions: {
            }
        }
    },
    computed: {
        sliderItem() {
            const data = this.dynamicData.model.dataSlider
            if(data === undefined) {
                return []
            }
            return data
        },
    }
}
</script>