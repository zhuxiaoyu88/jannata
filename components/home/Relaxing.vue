<template>
    <section class="relaxing" :style="{'background-image': `url(${model.featured.aws_file_url}/${model.featured.path}/${model.featured.filename.big})`}">
        <div class="relaxing__content">
            <h3 class="title relaxing__title" v-html="model.title">
            </h3>
            <div class="ornament__green-line"></div>
            <p class="relaxing__description">
                {{ model.description }}
            </p>
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