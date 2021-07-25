<template>
  <div class="black-bg" v-if="isModalOpen">
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <p>상세페이지 내용임</p>
      <button @click="isModalOpen=false">닫기</button>
    </div>
  </div>
  <div class="menu">
    <a v-for="(menu,index) in menus" :key="index">
      {{menu}}
    </a>
  </div>
  <div>
    <div v-for="data in onerooms" :key="data.id">
      <img :src="data.image" class="room-img">
      <h4>{{data.title}}</h4>
      <p>{{data.price}}원</p>
      <p>{{data.content}}</p>
    </div>
  </div>
</template>

<script>
import data from './oneroom';

export default {
  name: 'App',
  data(){
    return {
      onerooms : data,
      isModalOpen : false,
      신고수 : [0,0,0],
      menus:['Home','Shop','About'],
      products: data,
    }
  },
  methods:{
    increase(num){
      this.신고수[num]+=1;
    }
  },
  components: {
    
  }
}
</script>

<style>
body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

.black-bg{
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed; padding: 20px;
} 
.white-bg{
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}

.room-img{
  width: 100%;
  margin-top: 40px;
}
.menu{
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a{
  color: white;
  padding: 10px;
  font-weight: 700;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
