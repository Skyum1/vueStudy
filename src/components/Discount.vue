<template>
  <div class="discount">
    <h4>지금 결제하면 {{ disCountValue }}% 할인</h4>
  </div>
</template>

<script>
export default {
  name: 'DiscountVue',
  data() {
    return {
      disCountValue : 30,
    }
  },
  mounted() {
    setInterval(()=> {
      this.disCountValue--;
    },1000);
  }
}
</script>

<style>

</style>