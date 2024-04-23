<template>
  <div>
    <img :src="product.image" class="room-img" alt="x">
    <h4 @click="send">{{ product.title }}</h4>
    <p>{{ product.price }} 원</p>
  </div>
</template>

<script>
export default {
  name: 'CardVue',
  props: {
    product: Object,
  },
  methods : {
    send() {
      this.$emit('openModal', this.product.id)
    }
  }
}
</script>

<style>

</style>