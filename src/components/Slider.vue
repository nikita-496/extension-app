<script>
import 'vue3-carousel/dist/carousel.css'
import { Carousel, Slide, Pagination, Navigation } from 'vue3-carousel'

import create from '../assets/create-wallet.png'
import main from '../assets/main.png'
import verify from '../assets/verify.png'
import sucess from '../assets/sucess.png'
import activity from '../assets/activity.png'

export default {
  name: 'App',
  components: {
    Carousel,
    Slide,
    Pagination,
    Navigation,
  },
  data() {
    return {
        sliders: [
        {
            id: 1,
            content: 'Preview',
            cover: create,
            alt: 'create wallet'
        },
        {
            id: 2,
            content: 'Preview',
            cover: main,
            alt: 'screen assets'
        },
        {
            id: 3,
            content: 'Preview',
            cover: verify,
            alt: 'screen verify'
        },
        {
            id: 4,
            content: 'Preview',
            cover: sucess,
            alt: 'screen sucess'
        },
        {
            id: 5,
            content: 'Preview',
            cover: activity,
            alt: 'screen activity'
        }
    ]
    }
  }
}
</script>

<template>

 <Carousel :autoplay="3000" :wrap-around="true">
    <Slide v-for="slide in sliders" :key="slide.id">
        <figure class="carousel__item">
        <img :srcset="slide.cover"
            :alt="slide.alt">
    </figure>
    </Slide>

    <template #addons>
      <Pagination />
    </template>
  </Carousel>
</template>

<style scoped>
   
   
</style>