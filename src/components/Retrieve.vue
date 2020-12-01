<template>
  <div>
    <h2>Retrieve Component Loaded</h2>
    <div>{{ namingScheme1.data }}</div>
    <Test
      v-for="namingScheme2 in namingScheme1"
      :key="namingScheme2.id"
      :userName="namingScheme2.user.name"
      :profileImage="namingScheme2.user.profile_image.small"
      :imageDescription="namingScheme2.description"
      :imgThumb="namingScheme2.urls.small"
      :altDescription="namingScheme2.alt_description"
      :likes="namingScheme2.likes"
      :color="namingScheme2.color"
    ></Test>
    <div>

    </div>
  </div>
</template>

<script>
import { onMounted, ref } from 'vue';
import Test from './Test'

let namingScheme1 = ref([]);
export default {
  components: {
    Test
  },
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
      const url = (process.env.VUE_APP_ROOT_URL)+'/photos/?client_id='+(process.env.VUE_APP_KEY);
      // console.log(url); /*Debug URL*/
      try {
        const res = await fetch(url);
        namingScheme1.value = await res.json();
        return namingScheme1;
      } catch (error) {
        console.log('ERROR',error);
        this.error = 'Failed to do stuff. Nothing to see here . . .'
      }
    }
    return {
      getData,
      namingScheme1
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