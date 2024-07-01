<template>
  <div class="black-bg" v-if="modal" @click="modal = false">
    <div class="white-bg">
      <h4>상세 페이지</h4>
      <p>내용</p>
    </div>
  </div>
  <div class="menu">
  </div>
  <img src="./assets/honey_blueMo.jpg" class="wrap-img">
  <div>
    <h4 class="red" @click="modal = true">{{ products[0] }}</h4>
    <p>50 원</p>
    <button @click="increase(0)">신고</button> <span>count: {{cnt[0]}}</span>
  </div>
  <div>
    <h4 class="red">{{ products[1] }}</h4>
    <p>40 원</p>
    <button @click="increase(1)">신고</button> <span>count: {{cnt[1]}}</span>
  </div>
  <div>
    <h4 class="red">{{ products[2] }}</h4>
    <p>30 원</p>
    <button @click="increase(2)">신고</button> <span>count: {{cnt[2]}}</span>
  </div>
</template>

<script>


export default {
  name: 'App',
  data() {
    return {
      modal:false,
      cnt:[0,0,0],
      menus: ['home', 'shop', 'about'],
      products: ['AA', 'BB', 'CC']
    }
  },
  methods:{
    increase(i) {
      this.cnt[i]++;
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

.wrap-img {
  height: 500px;
}
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg{
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed; 
  padding: 20px;
}
.white-bg {
  width:100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
</style>
