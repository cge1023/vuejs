<template>

  <div class="menu">
    <a v-for="i in menu" :key="i">{{i}}</a>
  </div>

  <!-- <div>
    <h4>{{ products[0] }}</h4>
    <p>50 만원</p>
    <button @click="count[0]++">허위매물신고</button> <span>신고수 : {{count[0]}}</span>
  </div>
  <div>
    <h4>{{ products[1] }}</h4>
    <p>60 만원</p>
    <button @click="count[1]++">허위매물신고</button> <span>신고수 : {{count[1]}}</span>
  </div>
  <div>
    <h4>{{ products[2] }}</h4>
    <p>70 만원</p>
    <button @click="count[2]++">허위매물신고</button> <span>신고수 : {{count[2]}}</span>
  </div> -->
  <div v-for="(j, a) in products" :key="j">
    <h4>{{j}}</h4>
    <button @click="count[a]++">허위매물신고</button> <span>신고수 : {{count[a]}}</span>
  </div>
</template>

<script>

export default {
  name: 'App',
  // 데이터 보관함
  data() {
    return {
      //여기에 데이터 보관 (object 형식)
      count : [0, 0, 0],
      menu : ['Home','Shop','About'],
      products : ['역삼동원룸','천호동원룸','마포구원룸']
    }
  },
  methods: {
    increase() {
      this.count++;
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
}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a { 
  color: white;
  padding: 10px;
}
</style>
