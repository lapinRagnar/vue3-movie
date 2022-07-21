<template>
  <div class="home">
    <div class="feature-card">
      <router-link to="/movie/tt0409591">
        <img class="featured-img" src="https://media.istockphoto.com/photos/spiral-galaxy-illustration-of-milky-way-picture-id481229372?k=20&m=481229372&s=612x612&w=0&h=r-vNa2_NRHAyaQJj6o2UlGTfa9Dju2M8NH1AIpk9oHQ=" alt="">
        <div class="detail">
          <h3>Naruto</h3>
          <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Quidem nemo, ducimus culpa repellendus sequi nulla? Alias sint, quo sequi veniam provident ipsum hic ad repellat adipisci, quidem aliquam asperiores quod?</p>
        </div>
      </router-link>
    </div>
  </div>
</template>

<script>


export default {
  name: 'HomeView',

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
}
</style>
