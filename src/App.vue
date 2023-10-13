<script setup lang="ts">
import { ref } from 'vue';
import practice1 from './components/practice1.vue';
let user = ref({
firstName: 'Taro',
lastName: 'Sato',
});
</script>

<template>

  <practice1  :user = "user" />
  親コンポーネントのprops の値: {{ user.firstName }}
</template>

<style scoped>
</style>
