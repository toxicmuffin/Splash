<template>
  <div>
    <h2>Colonize Component Loaded</h2>
    <Retrieve/>
    <button @click="clickThis()">Click Me!</button>
  </div>
</template>

<script>
import Retrieve from './Retrieve'
export default {
  components: {
    Retrieve
  },
  methods: {
    clickThis() {
      console.log(this.information);
    }
  }
}
</script>

<style>

</style>