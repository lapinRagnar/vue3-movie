<template>
  <header>
    <router-link to="/">
      <h1><span>Mes</span>Movies</h1>
    </router-link>
  </header>
  <main>
    <router-view/>
  </main>
</template>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Fira Sans', sans-serif;

  &::selection{
    background: transparentize($color: #42B883, $amount: 0.5);
  }
}
body{
  background-color: #35495E;
}
a{
  text-decoration: none;
}
header{
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px 15px;
  background-color: #2C3D4E;
  box-shadow: 0 0 16px rgb(0, 0, 0, 0.5);

  &:hover{
    box-shadow: 0 0 36px rgb(0, 0, 0, 0.7);
  }

  h1{
    color: white;
    font-size: 20px;
    span{
      color: #ceb02d
    }
  }
}
</style>
