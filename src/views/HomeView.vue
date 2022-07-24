<template>
  <div class="home">
    <div class="feature-card">
      <router-link to="/movie/tt0409591">
        <img class="featured-img" src="https://media.istockphoto.com/photos/spiral-galaxy-illustration-of-milky-way-picture-id481229372?k=20&m=481229372&s=612x612&w=0&h=r-vNa2_NRHAyaQJj6o2UlGTfa9Dju2M8NH1AIpk9oHQ=" alt="">
        <div class="detail">
          <h3>Naruto</h3>
          <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Quidem nemo, 
            ?</p>
        </div>
      </router-link>
    </div>

    <form @submit.prevent="searchMovives" class="search-box">
      <input type="text" placeholder="rechercher film ?" v-model="search" >
      <input type="submit" value="rechercher" >
    </form>

    <div class="movies-list">
      <div class="movie" v-for="(movie,i) in movies" :key="i">
        <router-link class="movie-link" to="'/movie/' + movie.imdbID">
          <div class="product-image">
            <img :src="movie.Poster" alt="movie poster">
            <div class="type">{{ movie.Type }}</div>
          </div>
          <div class="detail">
            <p class="y">{{ movie.Year }}</p>
            <h3>{{ movie.Title }}</h3>
          </div>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>

import {ref} from 'vue'
import env from '@/env'


export default {
  name: 'HomeView',
  setup(){
    const search = ref('')
    const movies = ref([])
    const searchMovives = () => {
      if(search.value != ''){
        console.log(search.value)
        console.log(`http://www.omdbapi.com/?t=${search.value}&apikey=${env.apikey}`)
        fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&s=${search.value}`)
          .then(response => response.json())
          .then(data => { 
            console.log(data);
            console.log("data.Search",data.Search)
            movies.value = data.Search
            search.value = ''
            console.log("film", movies);

          })
      }
    }

    return {
      search,
      movies,
      searchMovives
    }
  }
}
</script>

<style lang="scss">
.home{
  .feature-card{
    position: relative;

    .featured-img{
      display: block;
      width: 100%;
      height: 300px;
      object-fit: cover;

      position: relative;
      z-index: 0;
    }

    .detail{
      position: absolute;
      left: 0;
      right: 0;
      bottom: 0;
      background-color: rgb(0, 0, 0, 0.6);
      padding: 16px;
      z-index: 1;

      h3{
        color: white;
        margin-bottom: 16px;
      }

      p{
        color: white;
      }
    }
  }

  .search-box{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 16px;

    input{
      display: block;
      appearance: none;
      border: none;
      outline: none;
      background: none;

      &[type="text"]{
        width: 100%;
        color: #fff;
        background-color: #496583;
        font-size: 20px;
        padding: 10px 16px;
        border-radius: 8px;
        margin-bottom: 15px;
        transition: 0.4s;

        &::placeholder{
          color: #f3f3f3
        }

        &:focus{ 
          box-shadow: 1px 7px 10px rgba(111, 111, 31, 0.519);
        }
      }

      &[type="submit"]{
        width: 100%;
        max-width: 300px;
        background-color: #42b883;
        padding: 16px;
        border-radius: 8px;
        color: #fff;
        font-size: 20px;
        text-transform: uppercase;
        transition: 0.4s;

        &:active{
          background-color: #3b8070;
        }
      }
    }
  }

  .movies-list{
    display: flex;
    flex-wrap: wrap;
    margin: 0 8px;

    .movie{
      max-width: 50%;
      flex: 1 1 50%;
      padding: 16px 8px;

      .movie-link{
        display: flex;
        flex-direction: column;
        height: 100%;

        .product-image{
          position: relative;
          display: block;

          img{
            display: block;
            width: 100%;
            height: 275px;
            object-fit: cover;
          }

          .type{
            position: absolute;
            padding: 8px 16px;
            background-color: #42b883;
            color: #fff;
            bottom: 16px;
            left: 0px;
            text-transform: capitalize;
          }
        }

        .detail{
          background-color: #496583;
          padding: 16px 8px;
          flex: 1 1 100%;
          border-radius: 0 0 8px 8px;

          .y{
            color: #aaa;
            font-size: 14px;
          }

          h3{
            color: #fff;
            font-weight: 600;
            font-size: 18px;
          }
        }
      }
    }
  }

}
</style>
