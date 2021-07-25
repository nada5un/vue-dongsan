<template>
  <Modal :onerooms = "onerooms" :roomIdx = "roomIdx" :isModalOpen="isModalOpen"></Modal>
  <div class="menu">
    <a v-for="(menu,index) in menus" :key="index">
      {{menu}}
    </a>
  </div>
  <Discount></Discount>
  <Card v-for="(data,idx) in onerooms" :key="idx" :data="onerooms[idx]"></Card>
</template>

<script>
import data from './oneroom';
import Discount from './Discount.vue'
import Modal from './Modal.vue'
import Card from './Card.vue'

export default {
  name: 'App',
  data(){
    return {
      roomIdx : 0,
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
    Discount,
    Modal,
    Card
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
