<template>
  <div class="header">
    <ul class="header-button-left">
      <li>Cancel</li>
    </ul>
    <ul class="header-button-right">
      <li v-if="step == 1" @click="step++">Next</li>
      <li v-if="step == 2" @click="publish">Publish</li>
    </ul>
    <img src="./assets/logo.png" alt="" class="logo" />
  </div>

  <ContainerWrap :posts="instaData" :steps="step" :url="img" />

  <button v-if="step == 0" @click="more">더보기 {{ count }}</button>

  <div class="footer">
    <ul class="footer-button-plus">
      <input @change="upload" type="file" id="file" class="inputfile" />
      <label for="file" class="input-plus">+</label>
    </ul>
  </div>
</template>

<script>
import ContainerWrap from "./components/ContainerWrap.vue";
import instaData from "./assets/instaData.js";
import axios from "axios";

axios.post();

export default {
  name: "App",
  data() {
    return {
      instaData: instaData,
      count: 0,
      step: 0,
      img: "",
    };
  },
  methods: {
    more() {
      console.log(this.count);
      axios
        .get(`https://codingapple1.github.io/vue/more${this.count}.json`)
        .then((result) => {
          // 요청성공시 실행할 코드
          this.instaData.push(result.data);
          this.count += 1;
        });
    },
    upload(e) {
      let file = e.target.files;
      console.log(file[0]);
      let url = URL.createObjectURL(file[0]);
      console.log(url);
      this.img = url;
      this.step += 1;
    },
    publish() {
      var myPost = {
        name: "Kim Hyun",
        userImage: "https://placeimg.com/100/100/arch",
        postImage: `url`,
        likes: 36,
        date: "May 15",
        liked: false,
        content: "오늘 무엇을 했냐면요 아무것도 안했어요 ?",
        filter: "perpetua",
      };
      this.instaData.unshift(myPost);
    },
  },
  components: {
    ContainerWrap,
  },
};
</script>

<style>
body {
  margin: 0;
}
ul {
  padding: 5px;
  list-style-type: none;
}
.logo {
  width: 22px;
  margin: auto;
  display: block;
  position: absolute;
  left: 0;
  right: 0;
  top: 13px;
}
.header {
  width: 100%;
  height: 40px;
  background-color: white;
  padding-bottom: 8px;
  position: sticky;
  top: 0;
}
.header-button-left {
  color: skyblue;
  float: left;
  width: 50px;
  padding-left: 20px;
  cursor: pointer;
  margin-top: 10px;
}
.header-button-right {
  color: skyblue;
  float: right;
  width: 50px;
  cursor: pointer;
  margin-top: 10px;
}
.footer {
  width: 100%;
  position: sticky;
  bottom: 0;
  padding-bottom: 10px;
  background-color: white;
}
.footer-button-plus {
  width: 80px;
  margin: auto;
  text-align: center;
  cursor: pointer;
  font-size: 24px;
  padding-top: 12px;
}
.sample-box {
  width: 100%;
  height: 600px;
  background-color: bisque;
}
.inputfile {
  display: none;
}
.input-plus {
  cursor: pointer;
}
#app {
  box-sizing: border-box;
  font-family: "consolas";
  margin-top: 60px;
  width: 100%;
  max-width: 460px;
  margin: auto;
  position: relative;
  border-right: 1px solid #eee;
  border-left: 1px solid #eee;
}

.content {
  display: none;
  width: 100%;
  height: 100px;
  line-height: 100px;
  text-align: center;
  background-color: #ccc;
}
.content.on {
  display: block;
}

.btn {
  width: calc(100% / 3);
  border: 0;
  padding: 10px 20px;
}
.btn.is_selected {
  background-color: #888;
  color: #fff;
}
</style>