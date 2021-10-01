<template>
    <section>
        <div class="relaxing">
            <div class="relaxing__background" data-scroll data-scroll-speed="-2" :style="{'background-image': `url(${model.featured.aws_file_url}/${model.featured.path}/${model.featured.filename.big})`}"></div>
            <div class="container">
                <div class="column-wrapper">
                    <div class="content content--type-1 content--white position-absolute">
                        <div class="content__inner">
                            <h3 class="content__title" v-html="model.title">
                            </h3>
                            <div class="ornament_line"></div>
                            <div class="content__description content__description--set-width" v-html="model.description">
                            </div>
                            <a :href="model.link.url" class="content__link">{{ model.link.title }}</a>
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