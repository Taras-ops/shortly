<script setup>
defineProps({
  iconName: String,
  title: String,
  description: String,
});
</script>

<template>
  <div class="statistic-card">
    <div class="statistic-card-icon">
      <img :src="`/src/assets/${iconName}`" />
    </div>
    <p class="statistic-card-title">{{ title }}</p>
    <p>{{ description }}</p>
  </div>
</template>
