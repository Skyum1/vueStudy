<template>
  <div class="black-bg" v-if="modalOpen">
    
    <div class="white-bg">
      <h4>{{ onerooms[selectIdx].title }}</h4>
      <img :src="onerooms[selectIdx].image" class="room-img" alt="x">
      <p>{{onerooms[selectIdx].content}}</p>
      <input v-model.number="month">
      <!-- <textarea></textarea> -->
      <!-- <select v-model="month">
        <option>1</option>
        <option>2</option>
        <option>3</option>
      </select> -->
      <p>  {{ month }} 개월 선택함 : {{ onerooms[selectIdx].price * month }} 원</p>
      <button @click="$emit('closeModal')">닫기</button>
      <!-- <button @click="modalOpen=false;">닫기</button> -->
    </div>
  </div>
</template>

<script>

export default {
  name: 'ModalVue',
  data() {
    return {
      month : 1,
    }
  },
  watch : {
    month(a) {
      if(isNaN(a) == true) {
        alert("숫자만 입력 가능합니다.");
        this.month = 1;
      }
      if(a > 12) { 
        alert("12보다 크면 안됨");
        this.month = 1;
      }
    }
  },
  props : {
    onerooms : Array,
    selectIdx : Number,
    modalOpen : Boolean,
  },
  components : {
  },
  updated() {
    if(this.month == 2) alert("2개월은 안됨!!!");
  }
}
</script>

<style>

</style>