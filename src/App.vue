<script lang="ts">
export default {
  data() {
    return { content: { header: "Vue.js Todo list" } };
  },
};
</script>

<template>
  <main>
    <section>
      <header>
        <h1>{{ content.header }}</h1>
      </header>
    </section>
  </main>
</template>
