<script lang="ts">
export default {
  data() {
    return {
      content: {
        header: "Vue.js Todo list",
        inputLabel: "Todo name",
        inputPlaceholder: "e.g. Create Vue.js app",
        buttonText: "Add new Todo item",
        listHeader: "Todos:",
      },
      inputValue: "",
      todos: [],
    };
  },
  methods: {
    appendToDoList() {
      this.todos.push(this.inputValue);
      this.inputValue = "";
    },
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

    <section>
      <label
        >{{ content.inputLabel }}
        <input :placeholder="content.inputPlaceholder" v-model="inputValue" />
      </label>

      <button @click="appendToDoList">{{ content.buttonText }}</button>
    </section>

    <section>
      <header>
        <h2>{{ content.listHeader }}</h2>
      </header>

      <ul>
        <li :key="todo" v-for="todo in todos">
          {{ todo }}
        </li>
      </ul>
    </section>
  </main>
</template>
