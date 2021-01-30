<template>
  <div class="about">
    <div class="weather">
      <h1 class="weather-title">{{ name }}の天気情報</h1>
      <ul>
        <li>天気：{{ main }}</li>
        <li>温度：{{ temp }}℃</li>
        <li>湿度：{{ humidity }}％</li>
        <li>風速：{{ speed }}ｍ</li>
      </ul>
      <a @click="$router.push({ name: 'Home'})" class="cp_btn">button</a>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  props: ["city"],
  data() {
    return {
      name: "",
      main: "",
      temp: "",
      humidity: "",
      speed: ""
    };
  },
  async created() {
    const item = await axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=a15c2fbe6d41688715e088c6cbe159ec`);
    console.log(item)
    const wD = item.data;
    this.name = wD.name;
    this.main = wD.weather[0].main;
    this.temp = wD.main.temp;
    this.humidity = wD.main.humidity;
    this.speed = wD.wind.speed;
  }
};
</script>


<style scoped>
.about {
  color: #fff;
  background: url("https://coachtech-video.s3-ap-northeast-1.amazonaws.com/liane-metzler-Y1ByvAGQ5iE-unsplash+(1).jpg")
  no-repeat;
  background-size: cover;
  width: 100vw;
  height: 100vh;
}

.weather {
  width: 620px;
  margin: 0 auto;
  padding-top: 100px;
}
.weather-title {
  font-size: 65px;
}

.weather li {
  font-size: 24px;
  margin-top: 20px;
  margin-left: 30px;
  
}

.cp_btn {
  color: red;
  border: 2px solid red;
  display: block;
  width: 600px;
  padding: 10px;
  text-align: center;
  text-decoration: none;
  border-radius: 3px;
  margin-top: 50px;
  cursor: pointer;
  transition: 0.4s;
}

.cp_btn:hover {
  background: red;
  color: #fff;
}

</style>
