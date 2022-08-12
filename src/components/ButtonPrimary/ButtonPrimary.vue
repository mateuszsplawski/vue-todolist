<script lang="ts">
export default {
  props: ["content", "handleClick", "type"],
};
</script>

<template>
  <button :type="type = button" @click="handleClick">{{ content }}</button>
</template>
