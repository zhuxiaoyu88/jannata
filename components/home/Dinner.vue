<template>
    <section class="section-big-padding bg-grey dinner">
        <div class="container">
            <div class="column-wrapper">
                <div class="col col-md-6">
                    <div class="box-img">
                        <picture class="img-overlap__container">
                            <source media="(min-width:768px)" :srcset="`${model.featured.aws_file_url}/${model.featured.path}/${model.featured.filename.big}`">
                            <source media="(max-width:767px)" :srcset="`${model.featured.aws_file_url}/${model.featured.path}/${model.featured.filename.medium}`">
                            <img data-scroll data-scroll-speed="-2" data-scroll-trigger-img :src="`${model.featured.aws_file_url}/${model.featured.path}/${model.featured.filename.big}`" :alt="`${model.title_one} ${model.title_two}`" class="img-overlap__img">
                        </picture>
                    </div>
                </div>
                <div class="col col-md-6">
                    <div data-scroll-trigger class="content content--grey">
                        <div class="content__inner">
                            <h3 class="content__title">
                                {{ model.title_one }} <br> <span class="text-green">{{ model.title_two }}</span>
                            </h3>
                            <div class="ornament_line"></div>
                            <div class="content__description content__description--set-width" v-html="model.description">
                            </div>
                            <a :href="model.link.url" class="content__link content__link--variant-green">{{ model.link.title }}</a>
                        </div>
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