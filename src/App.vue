<template>
  <div>
    <ul>
      <li v-for="recipe in recipes" :key="recipe.id">
        {{ recipe.id }} - {{ recipe.name }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      recipes: [],
    };
  },
  mounted() {
    this.fetchRecipes();
  },
  methods: {
    fetchRecipes() {
      const apiUrl = '/modu-calorie-backend-main/api/recipes_file';

      axios.get(apiUrl)
        .then(response => {
          this.recipes = response.data;
        })
        .catch(error => {
          console.error(error);
        });
    },
  },
};
</script>


<style>

</style>
