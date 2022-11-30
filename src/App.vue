<template>
  <div class="menu" >
      <a v-for="i in menu" :key="i">{{ i }}</a>
  </div>

  <Discount v-if="showDiscount == true"/>
  <button @click="priceAsc" class="btn">가격낮은 순 정렬</button>
  <button @click="priceDesc" class="btn">가격높은 순 정렬</button>
  <button @click="ganada" class="btn">상품명 가나다 순 정렬</button>
  <button @click="reset" class="btn">되돌리기</button>
  <Transition name="fade">
    <Modal @closeModal = "modal = false" :onerooms="onerooms" :clicked="clicked" :modal="modal"/>
  </Transition>
  <Card @openModal="modal = true; clicked=$event" v-for="(a, i) in onerooms" :key="i" :oneroom="onerooms[i]"/>
</template>

<script>
import data from "./assets/oneroom"
import Discount from './Discount.vue';
import Modal from "./Modal.vue"
import Card from "./Card.vue"

export default {
  name: 'App',
  data() {
    return {
      showDiscount: true,
      clicked: 0,
      oneroomsOriginal: [...data],
      onerooms: data,
      modal: false,
      count: [0, 0, 0],
      products: ['역삼동 원룸', '천호동 원룸', '마포구 원룸'],
      menu: ['Home', 'Products', 'About']

    }
  },
  methods: {
    increase() {
      this.count++;    },
    priceAsc() {
      this.onerooms.sort(function(a, b){
        return a.price - b.price
      })
    },
    priceDesc() {
      this.onerooms.sort(function(a, b){
        return b.price - a.price
      })
    },
    ganada() {
      this.onerooms.sort(function(a, b){
        return (a.title < b.title) ? -1 : (a == b) ? 0 : 1 
      })
    },
    reset() {
      this.onerooms = [...this.oneroomsOriginal]
    }
  },
  components: {
    Discount,
    Modal,
    Card
  }
}
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  margin: auto;
  width: 70%;
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
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}.menu a {
  color: white;
  padding: 10px;
}
.menu a:hover{
  cursor: pointer;
  font-weight: bolder;
}
.room-img {
  width: 100%;
  margin-top: 40px;
}
.close-btn, .btn {
  background: darkslateblue;
  color: white;
  border: none;
  border-radius: 5px;
  padding: 5px 10px; 
}
.close-btn:hover, .btn:hover{
  cursor: pointer;
}
.btn {
  margin-left: 20px;
  margin-top: 20px;
}
.modal-img {
  width: 70%;
}
.discount {
  background: #eee;
  padding: 20px;
  margin: 10px;
  border-radius: 5px;
}
.title:hover { 
  cursor: pointer;
}
.start {
  opacity: 0;
  transition: all 1s;
}
.end {
  opacity: 1;
}
.fade-enter-from{
  opacity: 0;
}
.fade-enter-active{
  transition: all 1s;
}
.fade-enter-to{
  opacity: 1;
}
.fade-leave-from{
  opacity: 1;
}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  opacity: 0;
}
</style>
