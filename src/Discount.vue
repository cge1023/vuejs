<template>
  <div class="discount">
    <h3>지금 결제하면 {{ discount }}% 할인</h3>
  </div>
</template>

<script>
export default {
    name: 'Discount',
    data() {
      return {
        showDiscount: true,
        discount: 30
      }
    },
    mounted() {
      setInterval(()=>{ 
        if (this.discount > 0) this.discount--
        else clearInterval();
      }, 1000)
  }
}
</script>

<style>

</style>