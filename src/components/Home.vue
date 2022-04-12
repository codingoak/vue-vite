<template>
  <h1 class="font-extrabold text-3xl mb-6">Home</h1>
  <p class="mb-6">Name in store is: {{ name }}</p>
  <input
    v-model="newName"
    type="text"
    class="p-2 border border-gray-600 rounded mr-4"
  />
  <button @click="saveName" class="text-white bg-indigo-600 p-2 rounded">
    Submit
  </button>
</template>

<script setup>
import { computed, ref } from 'vue';
import { useStore } from 'vuex';
import { useRouter } from 'vue-router';

const store = useStore();
const router = useRouter();
const newName = ref('');
const name = computed(() => {
  return store.state.user.name;
});

function saveName() {
  store.dispatch('saveName', newName.value);
  newName.value = '';
  router.push('/about');
}
</script>
