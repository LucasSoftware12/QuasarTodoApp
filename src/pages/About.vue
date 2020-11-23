<template>
  <q-page class="q-pa-lg">
    <h5 class="q-mt-none">About</h5>
    <div class="q-pa-md">
    <div class="q-gutter-md">
      <q-carousel
        v-model="slide"
        transition-prev="scale"
        transition-next="scale"
        swipeable
        animated
        control-color="white"
        navigation
        padding
        arrows
        height="300px"
        class="bg-primary text-white shadow-1 rounded-borders"
      >
        <q-carousel-slide name="style" class="column no-wrap flex-center">
          <q-icon name="account_circle" size="150px" />
          <div class="q-mt-md text-center">
            <a class="text-white text-weight-bold" href="https://www.linkedin.com/in/lucas-softw/">Linkedin</a>
          </div>
        </q-carousel-slide>
        <q-carousel-slide name="tv" class="column no-wrap flex-center">
          <q-icon name="live_tv" size="150px" />
          <div class="q-mt-md text-center">
            <a class="text-white text-weight-bold" href="https://github.com/LucasSoftware12">Github</a>
          </div>
        </q-carousel-slide>
        <q-carousel-slide name="layers" class="column no-wrap flex-center">
          <q-icon name="layers" size="150px" />
          <div class="q-mt-md text-center">
            <a class="text-white text-weight-bold" href="https://drive.google.com/file/d/1PLkmzK8aI2AQcxN3fy2lgkp_h1hfiXKK/view?usp=sharing">Resume</a>
          </div>
        </q-carousel-slide>
      </q-carousel>
    </div>
  </div>
  </q-page>
</template>

<script>
export default {
  data () {
    return {
      slide: 'style',
      lorem: 'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Itaque voluptatem totam, architecto cupiditate officia rerum, error dignissimos praesentium libero ab nemo.'
    }
  }
}
</script>
