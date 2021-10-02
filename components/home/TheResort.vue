<template>
    <section class="section-big-padding bg-grey the-resort">
        <div class="container">
            <div class="column-wrapper">
                <div class="col col-md-6 order-md-2 align-self-center">
                    <div class="content content--grey">
                        <div class="the-resort__bg-content">
                        </div>
                        <div data-scroll-trigger-text class="content">
                            <h3 class="content__title" v-html="model.title"></h3>
                            <div class="content__description content__description--set-width" v-html="model.description"></div>
                            <a class="content__link content__link--variant-green" :href="model.link.url">{{ model.link.title }}</a>
                        </div>
                    </div>
                </div>
                <div class="col col-md-6">
                    <div class="box-img">
                        <picture class="img-overlap__container">
                            <source media="(min-width:768px)" :srcset="`${model.featured.aws_file_url}/${model.featured.path}/${model.featured.filename.big}`">
                            <source media="(max-width:767px)" :srcset="`${model.featured.aws_file_url}/${model.featured.path}/${model.featured.filename.medium}`">
                            <img data-scroll data-scroll-speed="-2" data-scroll-trigger-img :src="`${model.featured.aws_file_url}/${model.featured.path}/${model.featured.filename.big}`" :alt="model.title" class="img-overlap__img">
                        </picture>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
export default {
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
    computed: {
        model() {
            const data = this.dynamicData.model
            if(data === undefined) {
                return {}
            }
            return data
        },
    }
}
</script>