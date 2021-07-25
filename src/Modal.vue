<template>
  <div class="black-bg" v-if="isModalOpen">
    <div class="white-bg">
      <img :src="onerooms[roomIdx].image" class="room-img">
      <h4>{{onerooms[roomIdx].title}}</h4>
      <p>{{onerooms[roomIdx].content}}</p>
      <input v-model="month">
      <p>{{month}}개월 선택함 :{{onerooms[roomIdx].price * month}}원</p>
      <button @click="closeModal">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
    name: 'Modal',
    data(){
        return {
            month: 1,
        }
    },
    watch:{
        month(a){
            //글자라면
            if(isNaN(a)){
                alert("글자 안됨");
                this.month = 1;
            }           
        }
    },
    beforeUpdate(){
        if(this.month==2){
            alert("2개월은 안됩니다");
            this.month=3;
        }
    },
    props:{
        onerooms: Array,
        roomIdx : Number,
        isModalOpen: Boolean,
    },
    methods:{
        closeModal(){
            this.$emit('closeModal');
        }
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