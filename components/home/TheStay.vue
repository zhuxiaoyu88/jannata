<template>
    <section class="section-big-padding bg-dark-grey the-stay">
        <div class="container">
            <div class="main-content">
                <div class="column-wrapper justify-md-content-end">
                    <div class="col col-md-6">
                        <div data-scroll-trigger-text class="content content--semi-grey">
                            <h3 class="content__title">
                                {{ dynamicData.model.title }}
                            </h3>
                            <div class="content__description" v-html="dynamicData.model.description">
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="properties-recommendation">
                <div class="column-wrapper">
                    <div v-for="item,id in sliderItem" :key="id" class="col col-md-4">
                        <a :href="item.link.url" class="property__link">
                            <h4 class="property__title">
                                {{ item.link.title }}
                            </h4>
                            <div class="property__img" :style="{'background-image': `url(${item.featured.aws_file_url}/${item.featured.path}/${item.featured.filename.big})`}">
                                <div class="property__img__on-hover" :style="{'background-image': `url(${item.featured_hover.aws_file_url}/${item.featured_hover.path}/${item.featured_hover.filename.big})`}">
                                </div>
                            </div>
                        </a>
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