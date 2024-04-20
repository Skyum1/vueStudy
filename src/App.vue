<template>  
  <div class="black-bg" v-if="modalOpen">
    <div class="white-bg">
      <h4>{{ onerooms[selectIdx].title }}</h4>
      <img :src="onerooms[selectIdx].image" class="room-img" alt="x">
      <p>{{onerooms[selectIdx].content}}</p>
      <p>{{ onerooms[selectIdx].price }} 원</p>
      <button @click="modalOpen=false;">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{ menu }}</a>
  </div>

  <Discount/>

  <div v-for="(product,i) in onerooms" :key="product.id">
    <img :src="product.image" class="room-img" alt="x">
    <h4 @click="modalOpen=true; selectIdx=i">{{ product.title }}</h4>
    <p>{{ product.price }} 원</p>
  </div>
</template> 

<script>
import data from './data/oneroom.js';
import Discount from './components/Discount.vue';

export default {
  name: 'App',
  data() {
    return {
      onerooms : data,
      selectIdx : 0,
      modalOpen : false,
      menus : ['Home', 'Shop', 'About'],
      products : [{name:'역삼동원룸', price:60, alert:0, img:'images/room0.jpg'},
      {name:'천호동원룸', price:90, alert:0, img:'images/room1.jpg'},
      {name:'송정동원룸', price:40, alert:0, img:'images/room2.jpg'},
      ],
    }
  },
  methods: {
    increase(product) {
      product.alert++;
    },
    getIconPath (iconName) {
      return iconName ? require(`./assets/${iconName}`) : '';
    }
  },
  components: {
    Discount : Discount,
  }
}
</script>

<style>

body {
  margin: 0;
}

div {
  box-sizing : border-box;
}

.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed;
  padding: 20px;
}

.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background : darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

.room-img {
  width: 100%;
  margin-top: 40px;
}
</style>
