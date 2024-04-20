<template>  
  <Modal :onerooms="onerooms" :selectIdx="selectIdx" :modalOpen="modalOpen"/>

  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{ menu }}</a>
  </div>

  <Discount/>

  <Card :product="product" v-for="product in onerooms" :key="product.id"/>
</template> 

<script>
import data from './data/oneroom.js';
import Discount from './components/Discount.vue';
import ModalVue from './components/Modal.vue';
import CardVue from './components/Card.vue';

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
    Modal : ModalVue,
    Card : CardVue
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
