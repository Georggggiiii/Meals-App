<template>
  <div class="image">
  <router-link :to="`/about/${meal.idMeal}`"><img :src="meal.strMealThumb" alt=""></router-link>
   <div class="desc">
    <h3>{{ meal.strMeal }}</h3>
   <a :href="meal.strYoutube" target="blank"><button class="youtube-button">YouTube</button></a>
   </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    meal: {
      required:true
    }
  }
}
</script>

<style scoped>
.image {
  width: 350px;
  border-radius: 15px;
}
.image img {
  width: 350px;
  height: 300px;
  padding: 30px 0;
  border-radius: 15px;
}
.desc {
  line-height: 35px;
  padding-bottom:15px;
}
.youtube-button {
  padding: 10px 15px;
  background-color: red;
  border:none;
  border-radius: 8px;
  color: white;
  cursor: pointer;
}
@media only screen and (max-width: 365px) {
  .image{
    width:270px;
  }
  .image img {
    width:270px;
  }
}
@media only screen and (max-width: 320px) {
  .image{
    width:230px;
  }
  .image img {
    width:230px;
  }
}
</style>
