<template>
  <div class="post">
    <div class="post-header">
      <div class="profile">
        <img :src="props.post.userImage" alt="">
      </div>
      <span class="profile-name">{{ props.post.name }}</span>
    </div>
    <div class="post-body" :style="{ backgroundImage : `url(${props.post.postImage})` }"></div>
    <div class="post-content">
      <p>{{ props.post.likes }} Likes</p>
      <p><strong>{{ props.post.name }}</strong> {{ props.post.content }}</p>
      <p class="date">{{ props.post.date }}</p>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from 'vue'

const props = defineProps({
  post : Object,
})
</script>

<style>
.post {
  width: 100%;
}
.profile {
  background-image: url("https://placeimg.com/100/100/arch");
  width: 30px;
  height: 30px;
  background-size: 100%;
  border-radius: 50%;
  float: left;
  overflow: hidden;
}
.profile img{
  width: 100%;height: 100%;
}
.profile-name {
  display: block;
  float: left;
  padding-left: 10px;
  padding-top: 7px;
  font-size: 14px;
}
.post-header {
  height: 30px;
  padding: 10px;
}
.post-body {
  background-image: url("https://placeimg.com/640/480/animals");
  height: 450px;
  background-position: center;
  background-size: cover;
  overflow: hidden;
}
.post-body img {
  /* width: 100%; */
  height: 100%;
  object-fit: cover;
}
.post-content {
  padding-left: 15px;
  padding-right: 15px;
  font-size: 14px;
}
.date {
  font-size: 11px;
  color: grey;
  margin-top: -8px;
}
</style>