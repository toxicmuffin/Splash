<template>
  <div>
    <h2>Colonize Component Loaded</h2>
    <Retrieve/>
  </div>
</template>

<script>
import Retrieve from './Retrieve'
export default {
  components: {
    Retrieve
  },
}
</script>

<style scoped>
  div {
    border: 1px pink solid;
  }
</style>