<template>
  <div>
    <h2>Retrieve Component Loaded</h2>
    <div>{{ information }}</div>
    <button @click="doSomething">Click me!</button>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  data() {
    return {
      isLoading: false,
      error: null,
    }
  },
  methods: {
    doSomething() {
      console.log(this.information);
    }
  },
  setup() {
    const information = ref([]);
    // populates the page with images
    async function getData() {
      // keys and urls are placed in .env - See .env_sample for details
      // const url = (process.env.VUE_APP_ROOT_URL)+'/photos/?client_id='+(process.env.VUE_APP_KEY);
      const url = ('https://reqres.in/api/users?page=2');
      // console.log(url); /*Debug URL*/
      try {
        const res = await fetch(url);
        const information = await res.json();
        console.log(information.data);
        return information;
      } catch (error) {
        console.log(error);
        this.error = 'Failed to do stuff. Nothing to see here . . .'
      }
    }
    return {
      getData,
      information
    }
  },
  mounted() {
    // runs function on life cycle hook and populates page
    this.getData();
    console.log(this.information);
    // console.log(this.information)
  }
}
</script>
