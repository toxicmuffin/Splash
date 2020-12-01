<template>
  <div>
    <div class="profile-details">
      <img class="profile-image" :src=profileImage alt="Users profile image">
      <h3>{{ userName }}</h3>
    </div>
      <p>{{ imageDescription }}</p>
      <img class="thumb-image" :src=imgThumb :alt=altDescription>
      <p>{{ likes }}</p>
      <p>{{ color }}</p>

  </div>
</template>

<script>
export default {
  props: ['userName', 'profileImage', 'imageDescription', 'imgThumb', 'altDescription', 'likes', 'color']
}
</script>

<style>
div {
  display: flexbox;
  flex-direction: column;
}
.profile-image {
  border-radius: 100%;
}
img {
  filter: grayscale(100%);
}
</style>