<template>
  <p :key="index" v-for="(data, index) in datax">{{ data.marca }}
      <button>
          <router-link :key="index" to="/info/">go</router-link>
      </button>
  </p>
  
</template>

<script>
import myData from "../assets/datax.json";

export default {
  data() {
    return {
      datax: myData,
    };
  },
};
</script>

<style>
</style>