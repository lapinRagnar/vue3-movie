<template>
  <div class="movie-detail">
    Detail {{ $route.params.id }}
    <h2> {{ movie.Title }} </h2>
    <p>{{ movie.Year }}</p>
    <p>{{ movie.Rating }}</p>
    <img :src="movie.Poster" alt="movie poster" class="featured-img">
    <p>{{ movie.Plot }}</p>

  </div>
</template>

<script>

import { ref, onBeforeMount } from 'vue'
import { useRoute } from 'vue-router'
import env from '@/env'

export default {
  setup(){
    const movie = ref({})
    const route = useRoute()

    onBeforeMount(() => {
      fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&i=${route.params.id}&plot=full`)
        .then(res => res.json())
        .then(data => {
          movie.value = data
        })
    })

    return {
      movie,
      route,
    }
  }

}
</script>

<style lang="scss">
.movie-detail{
  padding: 16px;

  h2{
    color: #fff;
    font-size: 28px;
    font-weight: 600;
    margin-bottom: 16px;
  }

  .featured-img{
    display: block;
    max-width: 200px;
    margin-bottom: 16px;
  }

  p{
    color: #fff;
    font-size: 18px;
    line-height: 1.4;  
    }
}
</style>