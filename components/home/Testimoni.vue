<template>
    <section class="testimoni bg-grey">
        <div class="container small-container">
            <flickity ref="flickity-testimoni" :options="flickityOptions">
                <div v-for="item,id in sliderItem" :key="id" class="carousel-cell">
                    <div class="testimoni__content">
                        <p class="testimoni__description">{{ item.description }}</p>
                        <h4 class="testimoni__title">{{ item.title }}</h4>
                    </div>
                </div>
            </flickity>
        </div>
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
    data(){
        return {
            flickityOptions: {
                prevNextButtons: false,
                adaptiveHeight: true
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