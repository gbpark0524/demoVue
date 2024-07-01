<template>
  <div class="menu">
    <a v-for="(menu,i) in menus" :key="i">{{ menu }} + {{i}}</a>
  </div>
  <div v-for="pro in products" :key="pro">
    <h4 class="red">{{ pro }}</h4>
    <p>50 원
    </p>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      menus : ['home', 'shop', 'about'],
      products : ['AA', 'BB', 'CC']
    }
  },
  components: {
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}
</style>
