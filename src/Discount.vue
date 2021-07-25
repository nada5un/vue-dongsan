<template>
    <div class="discount">
    <h4>지금 결제하면 {{salePercent}}% 할인</h4>
  </div>
</template>

<script>
export default {
    name: 'Discount',
    data(){
        return{
            salePercent: 30,
        }
    },
    mounted(){
        setInterval(()=>{
            if(this.salePercent>0){
                this.salePercent -= 1;
            }
        },1000);
  }
}
</script>

<style>
.discount{
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
</style>