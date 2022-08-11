<script lang="ts">
export default {
  props: ["content", "handleClick"],
};
</script>

<template>
  <button @click="handleClick">{{ content }}</button>
</template>
