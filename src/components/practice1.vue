<script setup lang="ts">
import { computed, ref } from 'vue';
const props = defineProps({
  user: Object,
});

// ref()に props の値を入れると、初期値を props の値にできる
const name = ref(props.user);
const firstName = ref(props.user.firstName);


const changeFirstName = function () {
  name.value.firstName = 'Hanako';
};
</script>

<template>
  <div>
    <span>オブジェクトの一部として変更: </span>
    <input type="text" v-model="name.firstName" />
  </div>
  <div>
    <span>プリミティブ値として変更: </span>
    <input type="text" v-model="firstName" />
  </div>
  <div>
    <span>関数からオブジェクトの一部を変更: </span>
    <button @click="changeFirstName">firstname を変える</button>
  </div>
  <div>子コンポーネントのprops の値: {{ user.firstName }}</div>
</template>
