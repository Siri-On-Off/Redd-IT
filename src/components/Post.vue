<script setup>
defineProps(["votes", "user", "title", "text", "id"]);
defineEmits(["voteUp", "voteDown"]);
</script>

<template>
  <div class="post">
    <span :class="{ 'post--trending': votes >= 10, 'post--spam': votes < 0 }">
      <div class="post__votes voter">
        <button @click="$emit('voteUp', id)" class="voter__action">👍</button>
        <div class="voter__votes">
          {{ votes }}
        </div>
        <button @click="$emit('voteDown', id)" class="voter__action">👎</button>
      </div>
      <div class="post__content">
        <div class="post__user">von {{ user }}</div>
        <div class="post__title">
          {{ title }}
        </div>
        <div class="post__text">
          {{ text }}
        </div>
      </div>
    </span>
  </div>
</template>

<style>
.post {
  display: flex;
  padding: 20px;
  border: 2px solid transparent;
}

.post--trending {
  border: 2px dashed #ecc500;
  background: #fff8ee;
}

.post--spam {
  opacity: 0.25;
}

.post + .post {
  border-top: 1px solid #fafafa;
}

.post__user {
  font-size: 0.9rem;
  color: #666;
  margin-bottom: 10px;
}

.post__title {
  font-size: 1rem;
  line-height: 1.1;
  font-weight: bold;
  margin-bottom: 10px;
}

.post__text {
  color: #666;
  line-height: 1.2;
  font-size: 0.9rem;
}

.post__votes {
  width: 40px;
  margin-right: 20px;
  display: flex;
  flex-shrink: 0;
  flex-direction: column;
  align-items: center;
}

.voter__votes {
  font-size: 1.2rem;
  font-weight: bold;
  margin: 8px 0;
}

.voter__action {
  appearance: none;
  background: none;
  font-weight: bold;
  border: none;
  cursor: pointer;
  font-size: 1.3rem;
  transition: background 0.2s ease;
  width: 30px;
  height: 30px;
  border-radius: 100%;
  line-height: 1;
}

.voter__action:hover {
  background: #f0f0f0;
}
</style>
