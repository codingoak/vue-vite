<template>
  <h1 class="font-bold <text-2xl mb-6">About: {{ name }}</h1>
  <button @click="backToHome" class="text-white bg-indigo-600 p-2 rounded">
    back to home
  </button>
</template>

<script setup>
import { computed } from 'vue';
import { useStore } from 'vuex';
import { useRouter } from 'vue-router';

const store = useStore();
const router = useRouter();
const name = computed(() => {
  return store.state.user.name;
});

function backToHome() {
  router.push('/');
}
</script>
