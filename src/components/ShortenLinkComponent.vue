<script setup>
import { ref } from 'vue';
import.meta.env.BITLY_ACCESS_TOKEN;

const shortenInputRef = ref(null);
const shortenItems = ref([]);
const copiedButton = ref(null);
const isInputEmpty = ref(false);

async function getShortenLink() {
  try {
    if (!shortenInputRef?.value || shortenInputRef?.value.length === 0) {
      isInputEmpty.value = true;
      return;
    }

    const result = await fetch('https://api-ssl.bitly.com/v4/shorten', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        Authorization: 'Bearer ' + import.meta.env.VITE_BITLY_ACCESS_TOKEN,
      },
      body: JSON.stringify({
        domain: 'bit.ly',
        long_url: shortenInputRef.value,
      }),
    });

    const data = await result.json();

    shortenItems.value.push({
      id: data.id,
      long_url: data.long_url,
      link: data.link,
    });

    shortenInputRef.value = '';
  } catch (err) {
    console.error(err);
  }
}

function onClickCopyButton(id) {
  copiedButton.value = id;

  const item = shortenItems.value.find((item) => item.id === id);
  navigator.clipboard.writeText(item.link);
}
</script>

<template>
  <div class="shorten-wrapper">
    <form @submit.prevent="getShortenLink" class="shorten-form">
      <div class="shorten-form-wrapper">
        <input
          v-model="shortenInputRef"
          placeholder="Shorten a link here..."
          type="text"
          :class="{ error: isInputEmpty }" />
        <button type="submit">Shorten it!</button>
      </div>
      <p v-if="isInputEmpty" class="shorten-form-error">Please add a link</p>
    </form>
    <div class="shorten-items-wrapper">
      <div class="shorten-item" v-for="item in shortenItems" :key="item.id">
        <a :href="item.long_url" _blank class="shorten-item-original-link">{{
          item.long_url
        }}</a>
        <div class="shorten-item-right-wrapper">
          <a :href="item.link" _blank class="shorten-item-formatted-link">{{
            item.link
          }}</a>
          <button
            @click="() => onClickCopyButton(item.id)"
            :class="{ active: copiedButton == item.id }">
            {{ copiedButton != item.id ? 'Copy' : 'Copied!' }}
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
