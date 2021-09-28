<template>
    <section class="section-big-padding bg-grey the-resort">
        <div class="container">
            <div class="row row-reverse">
                <div class="col col-md-6">
                    <div class="the-resort__bg-content">
                    </div>
                    <div class="the-resort__content">
                        <h3 class="title" v-html="model.title"></h3>
                        <a :href="model.link.url">{{ model.link.title }}</a>
                        <div v-html="model.description"></div>
                    </div>
                </div>
                <div class="col col-md-6">
                    <div class="the-resort__image-container">
                        <picture>
                            <source media="(min-width:768px)" :srcset="`${model.featured.aws_file_url}/${model.featured.path}/${model.featured.filename.big}`">
                            <source media="(max-width:767px)" :srcset="`${model.featured.aws_file_url}/${model.featured.path}/${model.featured.filename.medium}`">
                            <img :src="`${model.featured.aws_file_url}/${model.featured.path}/${model.featured.filename.big}`" :alt="model.description" class="banner__image">
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