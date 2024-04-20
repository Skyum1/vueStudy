<template>
  <div>
    <img :src="product.image" class="room-img" alt="x">
    <h4 >{{ product.title }}</h4>
    <p>{{ product.price }} 원</p>
  </div>
</template>

<script>
export default {
  name: 'CardVue',
  props: {
    product: Object
  }
}
</script>

<style>

</style>