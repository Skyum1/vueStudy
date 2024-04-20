<template>
  <div class="black-bg" v-if="modalOpen">
    <div class="white-bg">
      <h4>{{ onerooms[selectIdx].title }}</h4>
      <img :src="onerooms[selectIdx].image" class="room-img" alt="x">
      <p>{{onerooms[selectIdx].content}}</p>
      <p>{{ onerooms[selectIdx].price }} 원</p>
      <Discount/>
      <!-- <button @click="modalOpen=false;">닫기</button> -->
    </div>
  </div>
</template>

<script>
export default {
  name: 'ModalVue',
  data() {

  },
  props : {
    onerooms : Array,
    selectIdx : Number,
    modalOpen : Boolean,
  }
}
</script>

<style>

</style>