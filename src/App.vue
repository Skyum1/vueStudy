<template>  
  <transition name="fade">
    <Modal @closeModal="modalOpen = false"  :onerooms="onerooms" :selectIdx="selectIdx" :modalOpen="modalOpen"/>
  </transition>  

  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{ menu }}</a>
  </div>

  <Discount v-if="this.showDiscount == true"/>

  <button @click="priceSort">가격순정렬</button>
  <button @click="priceReverseSort">가격역순정렬</button>
  <button @click="titleSort">제목가나다정렬</button>
  <button @click="sortBack">되돌리기</button>

  <Card @openModal="modalOpen = true; selectIdx = $event" :product="product" v-for="product in onerooms" :key="product.id"/>
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
      showDiscount : true,
      oneroomsOriginal : [...data],
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
    priceSort() {
      this.onerooms.sort(function(a,b) {
        return a.price - b.price
      });
    },
    priceReverseSort() {
      this.onerooms.sort(function(a,b) {
        return b.price - a.price
      });
    },
    titleSort() {
      this.onerooms.sort((a,b) => {
        if(a.title > b.title) return 1;
        else return -1;
      });
    },
    sortBack() {
      this.onerooms = [...this.oneroomsOriginal];
    },

  },
  components: {
    Discount : Discount,
    Modal : ModalVue,
    Card : CardVue
  },

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

.fade-leave-from {
  opacity: 1;
}

.fade-leave-active {
  transition : all 1s;
}

.fade-leave-to {
  opacity: 0;
}

.fade-enter-from {
  transform: translateY(-1000px);
}

.fade-enter-active {
  transition : all 1s;
}

.fade-enter-to {
  transform: translateY(0px);
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
