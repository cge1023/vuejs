<template>
  <div class="black-bg" v-if="modal == true">
    <div class="white-bg">
      <img :src="onerooms[clicked].image" class="modal-img">
      <h4>{{ onerooms[clicked].title }}</h4>
      <p>{{ onerooms[clicked].content }}</p>
      <input placeholder="수량을 입력해주세요." v-model="month">
      <p>{{ month }} 개월 월세 : {{ onerooms[clicked].price * month }}원</p>
      <button @click="$emit('closeModal')" class="close-btn">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
    name: 'Modal',
    data() {
      return {
        month: 1,
      }
    },
    watch : {
      month(a) {
        if (isNaN(a) == true) {
          alert('개월수를 숫자로 입력해주세요')
          this.month = 1
        }
      }
    },
    props : {
        onerooms: Array,
        clicked: Number,
        modal: Boolean,
    },
    beforeUpdate() {
      if(this.month == 2) {
        alert("2개월 너무 적음.. 안팝니다")
        this.month = 3
      }
    }
}
</script>

<style>

</style>