<template>
  <div class="image-card">
    <div class="div-abs">
      <img class="profile-image" :src=profileImage alt="Users profile image">
      <h3 class="user-name">{{ userName }}</h3>
    </div>
    <img class="thumb-image" :src=imgThumb :alt=altDescription>
  </div>
</template>

<script>
export default {
  props: [
    'userName',
    'profileImage',
    'profileUrl',
    'imgThumb',
    'altDescription',
    ]
}
</script>

<style>
.thumb-image {
  width: 100%;
}
.thumb-image:hover{
  cursor: pointer;
}
.profile-image {
  border-radius: 100%;
  position: relative;
  left: 5px;
  top: 5px;
}
.user-name {
  display: inline;
  position: relative;
  color: #fff;
  left: 10px;
}
.div-abs {
  position: absolute;
}
a {
  text-decoration: none;
}
</style>