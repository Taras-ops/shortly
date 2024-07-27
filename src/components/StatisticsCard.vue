<script setup>
const props = defineProps({
  iconName: String,
  title: String,
  description: String,
});

function getImgUrl() {
  const url = '/icons/' + props.iconName + '.svg';
  return require(url);
}
</script>

<template>
  <div class="statistic-card">
    <div class="statistic-card-icon">
      <img :src="getImgUrl()" />
    </div>
    <p class="statistic-card-title">{{ title }}</p>
    <p>{{ description }}</p>
  </div>
</template>
