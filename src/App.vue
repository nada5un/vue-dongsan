<template>
  <transition name="fade">
    <Modal @closeModal="isModalOpen = false;" :onerooms = "onerooms" :roomIdx = "roomIdx" :isModalOpen="isModalOpen"></Modal>
  </transition>
  <div class="menu">
    <a v-for="(menu,index) in menus" :key="index">
      {{menu}}
    </a>
  </div>
  
  <Discount v-if="showDiscount"></Discount>

  <button @click="priceSort">가격낮은순정렬</button>
  <button @click="priceSortReverse">가격높은순정렬</button>
  <button @click="alphabetSort">가나다순정렬</button>
  <button @click="sortBack">되돌리기</button>
  <Card @OpenModal="isModalOpen = true; roomIdx=idx" :data="onerooms[idx]" v-for="(data,idx) in onerooms" :key="idx"></Card>
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
      oneroomsOrigin : [...data],
      isModalOpen : false,
      신고수 : [0,0,0],
      menus:['Home','Shop','About'],
      products: data,
      showDiscount: true,
    }
  },
  methods:{
    increase(num){
      this.신고수[num]+=1;
    },
    priceSort(){
      this.onerooms.sort(function(a,b){
        return a.price-b.price
      });
    },
    priceSortReverse(){
      this.onerooms.sort(function(a,b){
        return b.price - a.price
      });
    },
    alphabetSort(){
      this.onerooms.sort(function(a,b){
        return (a.title<b.title)?-1:(a.title==b.title)?0:1;
      });
    },
    sortBack(){
      this.onerooms = [...this.oneroomsOrigin];
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
/* 등장 */
.fade-enter-from{
  transform: translateY(-1000px);
}
.fade-enter-active{
  transition: all 1s;
}
.fade-enter-to{
  transform: translateY(0px);
}
/* 퇴장 */
.fade-leave-from{
  transform: translateY(0px);
}
.fade-leave-active{
  transition: all 1s;
}
.fade-leave-to{
  transform: translateY(-1000px);
}

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
