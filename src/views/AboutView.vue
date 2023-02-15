<template>
<div>
 <div class="title">
  <h1>{{ meal[0]?.strMeal }}</h1>
 </div>
  <div class="image">
    <img :src="meal[0]?.strMealThumb" alt="">
  </div>
<div class="d-flex">
  <p><strong>Category:</strong>{{ meal[0]?.strCategory }}</p>
  <p><strong>Area:</strong> {{ meal[0]?.strArea }}</p>
  <p><strong>Tags:</strong> {{ meal[0]?.strTags }}</p>
</div>
<div class="instruction">
  <p>{{ meal[0]?.strInstructions }}</p>
</div>
<div class="flex">
<div class="ingredients">
  <h2>Ingredients</h2>
    <div v-for="(el, ind) of new Array(20)" :key="ind">
    <li v-if=" meal[0]?.[`strIngredient${ind + 1}`]">
      {{ ind + 1 }} .{{ meal[0]?.[`strIngredient${ind + 1}`] }}
    </li>
  </div>
  
</div>
  
<div class="measures">
  <h2>Measures</h2>
<div v-for="(el, ind) of new Array(20)" :key="ind">
  <li v-if=" meal[0]?.[`strMeasure${ind + 1}`]">
    {{ ind + 1 }} .{{ meal[0]?.[`strMeasure${ind + 1}`] }}
  </li>
</div>

</div>
</div>
  <div class="buttons">
    <a :href="meal[0]?.strYoutube" target="blank"><button  class="youtube-button">YouTube</button></a>
    <a target="blank" :href="meal[0]?.strSource"><button class="source-button">View Original Source</button></a>
  </div>
</div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      meal:[],
    }
  },
  created() {
    axios
      .get(`https://www.themealdb.com/api/json/v1/1/lookup.php?i=${this.$route.params.id}`)
      .then(response => {
        this.meal = response.data.meals;
      })
      .catch(error => {
        console.error(error);
      });
  },
}
</script>

<style scoped>
.title {
  color:orange;
  margin-top:100px;
}
.title , .image{
  justify-content: center;
  display:grid;
}
li {
  list-style-type: none;
}
.d-flex {
  display:flex;
  justify-content: center;
  gap:100px;
  line-height:40px;
}
.instruction {
  width: 700px;
  margin: 0 auto;
}
.flex {
  display:flex;
  justify-content: center;
  margin-top:20px;
  margin: 0 auto;
}
.ingredients {
  position:relative;
  right:13%;
}
.measures {
  position:relative;
 left:13%;
}
.buttons {
  justify-content: center;
  display:flex;
  gap:26%;
  margin-top:20px;
}
.youtube-button {
  padding: 10px 15px;
  background-color: red;
  border:none;
  border-radius: 8px;
  color: white;
  cursor: pointer;
}
.source-button {
  padding: 10px 15px;
  border:none;
  border-radius: 8px;
  cursor: pointer;
}
@media only screen and (max-width: 800px) {
    img {
      width:100%;
      justify-content: center;
      display:grid;
      margin: 0 auto;
    }
    .instruction {
      width:550px;
    }
}
@media only screen and (max-width: 600px) {
    img {
      width:100%;
      justify-content: center;
      display:grid;
      margin: 0 auto;
    }
    .instruction {
      width:350px;
    }
    .d-flex {
      gap:10px;
    }
    .flex {
      display:grid;
    }
    .measures {
      transform:translateX(-100px);
    }
    .ingredients {
      transform:translateX(-60px);
    }
}
@media only screen and (max-width: 370px) {

  img {
      width:100%;
      justify-content: center;
      display:grid;
      margin: 0 auto;
    }
    .instruction {
      width:200px;
    }
    .d-flex {
      display:grid;
      grid-template-columns: 1fr;
      text-align: center;
    }
    .flex {
      display:grid;
    }
    .measures {
      transform:translateX(-30px);
    }
    .ingredients {
      transform:translateX(5px);
    }
}
</style>
