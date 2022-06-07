// eslint-disable-next-line
<template>
  <div>
    <div class="black-bg" v-if="isModal">
      <div class="white-bg">
        <img :src="oneroomData[clickNumber].image" style="width: 100%" />
        <h4>{{ oneroomData[clickNumber].title }}</h4>
        <p>가격 :{{ oneroomData[clickNumber].price }}</p>
        <p>내용 : {{ oneroomData[clickNumber].content }}</p>
        <button @click="isModal = false">닫기</button>
      </div>
    </div>
    <DiscountBanner />
    <nav class="menu">
      <a v-for="(el, idx) in 메뉴들" :key="idx">{{ el }}</a>
    </nav>

    <div v-for="(el, idx) in oneroomData" :key="idx">
      <img class="room-img" :src="el.image" @click="isModal = true" />
      <h4
        @click="
          isModal = true;
          clickNumber = idx;
        "
      >
        {{ el.title }}
      </h4>
      <p>{{ el.price }}원</p>
    </div>
  </div>
</template>

<script>
import data from "./assets/data";
import DiscountBanner from "./DiscountBanner.vue";

export default {
  name: "App",
  data() {
    return {
      clickNumber: 0,
      isModal: false,
      oneroomData: data,
      메뉴들: ["Home", "Shop", "About"],
      신고수: [0, 0, 0],
    };
  },
  methods: {
    increase(idx) {
      this.신고수[idx] += 1;
    },
  },
  components: {
    Discount: DiscountBanner,
  },
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
  width: 50%;
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

.white-bg {
  width: 100%;
  background: white;
  border-radius: 5px;
  padding: 20px;
}
</style>
