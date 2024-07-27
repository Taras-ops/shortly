<script setup>
import { ref } from 'vue';
import Button from './Button.vue';

const isMobNavShowed = ref(false);

function onClickBurger() {
  isMobNavShowed.value = !isMobNavShowed.value;
}
</script>

<template>
  <header class="header">
    <div class="container">
      <div class="header-wrapper">
        <div class="header-left">
          <div class="">
            <img src="../assets/logo.svg" alt="shortly" />
          </div>
          <nav class="header-nav" :class="{ show: isMobNavShowed }">
            <ul>
              <li><a href="">Features</a></li>
              <li><a href="">Pricing</a></li>
              <li><a href="">Resources</a></li>
            </ul>
            <div class="header-nav-btns">
              <a href="">Login</a>
              <Button text="Sign Up" />
            </div>
          </nav>
        </div>
        <div class="header-btns">
          <a href="">Login</a>
          <Button text="Sign Up" />
        </div>
        <div class="burger" @click="onClickBurger">
          <span></span>
        </div>
      </div>
    </div>
  </header>
</template>
