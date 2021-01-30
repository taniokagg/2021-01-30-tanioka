<template>
  <div class="card">
    <img class="card-img"
    src="https://coachtech-video.s3-ap-northeast-1.amazonaws.com/clouds-449822_640.jpg"
    />
    <div class="card-content">
      <h1 class="card-title">{{ city }}</h1>
    </div>
    <div class="card-link">
      <a @click="$router.push({name: 'About', params: {city: city }})">about</a>
    </div>
  </div>
</template>

<script>
export default {
  props: ["city"]
}
</script>

<style scoped>

.card {
width: 27%;
background: #fff;
border: 1px solid #eee;
border-radius: 5px;
box-shadow: 0 2px 5px #ccc;
margin: 30px 25px;
}

.card-title {
height: 90px;
line-height: 90px;
text-align: center;
border-bottom: 1px solid #eee;
font-size: 18px;
}

.card-link {
  padding: 25px;
  text-align: center;
}

.card-link a {
  color: #0bd;
  cursor: pointer;
  margin: 0 10px;
}
.card-link a:hover {
  color: #0090aa;
}

.card-img {
  max-width: 100%;
  border-radius: 8px 8px 0px 0px;
  height: auto;
}
</style>