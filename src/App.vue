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
        pendingListHeader: "Todos pending:",
        completedListHeader: "Todos completed:",
        deleteButtonText: "Delete",
        changeStatusText: "Change status",
      },
      inputValue: "",
      pendingTodos: [],
      completedTodos:[]
    };
  },
  methods: {
    appendTodoList() {
      const defaultStatus = "Pending";
      const newTodo = {
        content: this.inputValue,
        id: `${Math.random()} ${this.inputValue}`,
        status: defaultStatus,
      };

      this.pendingTodos.push(newTodo);
      this.inputValue = "";
    },
    removeTodoFromList(todo) {
      if(todo.status === "Pending"){
        const newTodos = this.pendingTodos.filter(({ id }) => id !== todo.id);
        this.pendingTodos = newTodos;
      } else {
        const newTodos = this.completedTodos.filter(({ id }) => id !== todo.id);
        this.completedTodos = newTodos; 
      }
    },
    changeTodoStatus(todo) {
      if(todo.status === "Pending"){
        this.completedTodos = [...this.completedTodos, {...todo, status: "Completed"}]
        this.pendingTodos = this.pendingTodos.filter(todo => todo === todo)
      } else {
        this.pendingTodos = [...this.pendingTodos, {...todo, status: "Pending"}]
        this.completedTodos = this.completedTodos.filter(todo => todo === todo)
      }
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
      <form @submit="$event.preventDefault()">
      <InputWithLabel
        :placeholder="content.inputPlaceholder"
        :label="content.inputLabel"
        v-model:value="inputValue"
      />

      <ButtonPrimary
        :type="submit"
        :content="content.buttonText"
        :handleClick="appendTodoList"
      />
      </form>
    </section>

    <section>
      <header>
        <h2>{{ content.pendingListHeader }}</h2>
      </header>

      <ul>
        <li :key="todo.id" v-for="todo in pendingTodos">
          <span>{{ todo.content }} {{ todo.status }}</span>

          <ButtonPrimary
            :content="content.deleteButtonText"
            :handleClick="() => removeTodoFromList(todo)"
          />

          <ButtonPrimary
            :content="content.changeStatusText"
            :handleClick="() => changeTodoStatus(todo)"
          />
        </li>
      </ul>
    </section>

    <section>
      <header>
        <h2>{{ content.completedListHeader }}</h2>
      </header>

      <ul>
        <li :key="todo.id" v-for="todo in completedTodos">
          <span>{{ todo.content }} {{ todo.status }}</span>

          <ButtonPrimary
            :content="content.deleteButtonText"
            :handleClick="() => removeTodoFromList(todo)"
          />

          <ButtonPrimary
            :content="content.changeStatusText"
            :handleClick="() => changeTodoStatus(todo)"
          />
        </li>
      </ul>
    </section>
  </main>
</template>
