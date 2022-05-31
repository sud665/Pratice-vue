<template>
  <nav class="menu">
    <a v-for="(el, idx) in 메뉴들" :key="idx">{{ el }}</a>
  </nav>
  <div v-for="(el, idx) in products" :key="idx">
    <img class="room-img" src="./assets/room0.jpg" />
    <h4>
      {{ products[idx] }}
      <p>{{ prices[idx] }}만원</p>
      <button @click="increase(idx)">허위매물신고</button>
      <span> 신고수 : {{ 신고수[idx] }}</span>
    </h4>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      메뉴들: ["Home", "Shop", "About"],
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
      prices: ["1000", "2000", "3000"],
      신고수: [0, 0, 0],
      image: ["./assets/room0.jpg", "./assets/room1.jpg", "./assets/room2.jpg"],
    };
  },
  methods: {
    increase(idx) {
      this.신고수[idx] += 1;
    },
  },
  components: {},
};
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

.menu {
  background: darkslateblue;
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

body {
  margin: 0;
}
div {
  box-sizing: border-box;
}

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}

.whith-bg {
  width: 100%;
  background: white;
  border-radius: 5px;
  padding: 20px;
}
</style>
