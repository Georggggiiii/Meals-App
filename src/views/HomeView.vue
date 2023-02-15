<template>
      <input v-model="searchTerm" @input="onInput" />
  <div class="home">
    <MealComp  v-for="meal in meals" :key="meal.idMeal" :meal="meal"/>
  </div>
</template>

<script>
import axios from 'axios';
import MealComp from '@/components/MealComp.vue'

export default {
  name: 'HomeView',
  data() {
    return {
      meals: [],
      searchTerm: '',
      timeout: null,
    }
  },
  components: {
    MealComp
  },
  methods: {
    search: function() {
      axios.get(`https://www.themealdb.com/api/json/v1/1/search.php?s=${this.searchTerm}`)
        .then(response => {
          this.meals = response.data.meals;
        })
        .catch(error => {
          console.error(error);
        });
    },
    onInput() {
        clearTimeout(this.timeout);
      this.timeout = setTimeout(() => {
        this.search();
      }, 500)
      },
  },
  created() {
    this.onInput();
  },
}
</script>

<style scoped>
input {
    border: 1px solid grey;
    outline: none;
    padding: 10px 15px;
    width: 50%;
    position: relative;
    left: 27%;
    margin-top: 150px;
   border-radius: 5px;
}
.home {
  display: grid;
  grid-template-columns:0.1fr 0.1fr 0.1fr;
  gap: 60px;
  justify-content: center;
}

@media only screen and (max-width: 1200px) {
  .home {
    grid-template-columns:0.1fr 0.1fr;
  }
}
@media only screen and (max-width: 800px) {
  .home {
    grid-template-columns:0.1fr;
  }
}
</style>