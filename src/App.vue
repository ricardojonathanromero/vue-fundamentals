<script setup>
import { ref, computed } from 'vue';

const favList = ref([]);
const counter = ref(0);

const increase = () => counter.value++;

const decrease = () => counter.value--;

const reset = () => counter.value = 0;

const addFav = () => favList.value.push(counter.value);

const colorCounter = computed(() => {
  switch (true) {
    case counter.value === 0: return 'text-light';
    case counter.value > 0: return 'text-success';
    default: return 'text-danger';
  }
});

const existNumberInFavList = computed(() => favList.value.lastIndexOf(counter.value) >= 0 );
</script>

<template>
  <h1>Solution</h1>
  <br>
  <br>
  <h2 :class="colorCounter">{{ counter }}</h2>
  <br>
  <button type="button" class="btn btn-primary ms-2" @click="increase">+</button>
  <button type="button" class="btn btn-danger ms-2" @click="decrease">-</button>
  <button type="button" class="btn btn-secondary ms-2" @click="reset">res</button>
  <button type="button" class="btn btn-secondary ms-2" :disabled="existNumberInFavList" @click="addFav">add</button>
  <br>
  <br>
  <br>
  <h2>Favorite numbers:</h2>
  <ul>
    <li v-for="(fav, index) in favList" :key="index">
      <span class="text-white" style="font-size: 1.5em;">{{ fav }}</span>
    </li>
  </ul>
</template>

<style />
