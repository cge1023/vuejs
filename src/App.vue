<template>
  <div>
    <img alt="Vue logo" src="./assets/logo.png">
  <div>
    <h4>{{products[0]}}</h4>
    <p>50 만원</p>
  </div>
  <div>
    <h4>{{products[1]}}</h4>
    <p>가격은 아무거나</p>
  </div>
  <div>
    <h4>{{products[2]}}</h4>
    <p>가격은 아무거나</p>
  </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  // 데이터 보관함
  data() {
    return {
      //여기에 데이터 보관 (object 형식)
      products : ['역삼동원룸','천호동원룸','마포구원룸']
    }
  },
  components: {
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
