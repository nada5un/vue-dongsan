<template>
  <div class="black-bg" v-if="isModalOpen">
    <div class="white-bg">
      <img :src="onerooms[roomIdx].image" class="room-img">
      <h4>{{onerooms[roomIdx].title}}</h4>
      <p>{{onerooms[roomIdx].content}}</p>
      <p>{{onerooms[roomIdx].price}}</p>
      <!-- <button @click="isModalOpen=false">닫기</button> -->
    </div>
  </div>
</template>

<script>
export default {
    name: 'Modal',
    props:{
        onerooms: Array,
        roomIdx : Number,
        isModalOpen: Boolean,
    }
}
</script>

<style>
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

</style>