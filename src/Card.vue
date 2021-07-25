<template>
  <div>
    <img :src="data.image" class="room-img">
    <h4 @click="openModal">{{data.title}}</h4>
    <p>{{data.price}}원</p>
  </div>
</template>

<script>
export default {
    name: 'Card',
    props:{
        data: Object,
    },
    methods:{
        openModal(){
           this.$emit('OpenModal');
        }
    }
}
</script>

<style>

</style>