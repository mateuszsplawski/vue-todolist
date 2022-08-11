<script>
import ButtonPrimary from "./components/Button/ButtonPrimary.vue";
import InputWithLabel from "./components/Input/InputWithLabel.vue";

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
      console.log(this.inputValue);
      this.todos.push(this.inputValue);
      this.inputValue = "";
    },
  },
  components: { ButtonPrimary, InputWithLabel },
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
      <InputWithLabel
        :placeholder="content.inputPlaceholder"
        :label="content.inputLabel"
        v-model:value="inputValue"
      />
      <ButtonPrimary
        :content="content.buttonText"
        :handleClick="appendToDoList"
      />
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
