<script>
import ButtonPrimary from "./components/ButtonPrimary/ButtonPrimary.vue";
import InputWithLabel from "./components/InputWithLabel/InputWithLabel.vue";

export default {
  data() {
    return {
      content: {
        header: "Vue.js Todo list",
        inputLabel: "Todo name",
        inputPlaceholder: "e.g. Create Vue.js app",
        buttonText: "Add new Todo item",
        listHeader: "Todos:",
        deleteButtonText: "Delete Todo item",
      },
      inputValue: "",
      todos: [],
    };
  },
  methods: {
    appendTodoList() {
      this.todos.push(this.inputValue);
      this.inputValue = "";
    },
    removeTodoFromList(todoKey) {
      const newTodos = this.todos.filter((todo) => todo !== todoKey);
      this.todos = newTodos;
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
        :handleClick="appendTodoList"
      />
    </section>

    <section>
      <header>
        <h2>{{ content.listHeader }}</h2>
      </header>

      <ul>
        <li :key="todo" v-for="todo in todos">
          <span>{{ todo }}</span>
          <ButtonPrimary
            :content="content.deleteButtonText"
            :handleClick="() => removeTodoFromList(todo)"
          />
        </li>
      </ul>
    </section>
  </main>
</template>
