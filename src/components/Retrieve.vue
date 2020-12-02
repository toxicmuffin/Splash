<template>
  <div class="card-holder">
    <CardLayout
      class="cards"
      v-for="namingScheme2 in namingScheme1"
      :key="namingScheme2.id"
      :userName="namingScheme2.user.name"
      :profileImage="namingScheme2.user.profile_image.small"
      :profileUrl="namingScheme2.links.self"
      :imgThumb="namingScheme2.urls.small"
      :altDescription="namingScheme2.alt_description"
    />
  </div>
</template>

<script>
import { onMounted, ref } from 'vue';
import CardLayout from './CardLayout'

let namingScheme1 = ref([]);
export default {
  components: {
    CardLayout
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

<style>
  .card-holder {
    max-width: 1300px;
    margin: 0 auto;
    width: 70%;
    display: grid;
  }
  .cards {
    width: 100%;
    transition: .3s ease-in-out;
  }
  @media only screen and (min-width: 800px) {
  .card-holder{
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: masonry;
    justify-content: center;
  }
  .cards {
    margin: 5px;
    width: 400px;
    filter: grayscale(100%);
  }
  .cards:hover {
    filter: grayscale(0);
  }
  }
</style>