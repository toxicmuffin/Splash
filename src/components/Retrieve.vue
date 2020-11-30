<template>
  <div>
    <h2>Retrieve Component Loaded</h2>
    <div>{{ information.data }}</div>
  </div>
</template>

<script>
import { onMounted, ref } from 'vue';
let information = ref([]);
export default {
  
  data() {
    return {
      isLoading: false,
      error: null,
    }
  },
  setup() {
    // populates the page
    onMounted(() => {
      getData();
    });
    async function getData() {
      // keys and urls are placed in .env - See .env_sample for details
      // const url = (process.env.VUE_APP_ROOT_URL)+'/photos/?client_id='+(process.env.VUE_APP_KEY);
      const url = ('https://reqres.in/api/users?page=2');
      // console.log(url); /*Debug URL*/
      try {
        const res = await fetch(url);
        information.value = await res.json();
        return information;
      } catch (error) {
        console.log('ERROR',error);
        this.error = 'Failed to do stuff. Nothing to see here . . .'
      }
    }
    return {
      getData,
      information
    }
  }
}
</script>

<style scoped>
  div {
    border: 1px green solid;
    border-radius: 15px;
  }
</style>