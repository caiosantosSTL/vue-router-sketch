<template>
  <div>
    <h1>Welcome to my lab area</h1>

    <div>
      <h1 :class="changeC">Text color</h1>
      <!-- bind back to front data info-->
    </div>

    <div>
      <p>Click to up number</p>
      <button @click="goup">Up here {{ count }}</button>
    </div>

    <div>
      <input v-model="text" placeholder="put here any text" />
      <p>{{ text }}</p>
    </div>

    <div>
      <button @click="toggle">change</button>
      <h3 v-if="awesome">Vue is amazing</h3>
      <h3 v-else>Nooooo</h3>
    </div>

    <div>
      <input v-model="newTodo" @keyup.enter="addTodo" />
      <button @click="addTodo">add</button>
      <ul v-for="todo in todos" :key="todo.id">
        <li>
          {{ todo.text }}
          <button @click="removeTodo2">delete</button>
        </li>
      </ul>
    </div>

    <div>
      <p ref="px">Loading ...</p>
    </div>

    <div>
      <p>Todo id: {{ todoId }}</p>
      <button @click="todoId++">Fetch next todo</button>
      <p v-if="!todoData">Loading...</p>
      <pre v-else>{{ todoData }}</pre>
    </div>

    <div>
      <Slotxx> {{ msg }} </Slotxx>
      <PropsT :text="myvalue"></PropsT>
    </div>
  </div>
</template>

<script>
import Slotxx from "../components/Slotx.vue";
import PropsT from "../components/PropsT.vue"

let id = 0;

export default {
  components: {
    Slotxx,
    PropsT
  },
  data() {
    return {
      msg: "from parent",
      myvalue: "This value going to component",
      changeC: "vv",
      count: 0,
      text: "",
      awesome: true,
      newTodo: "",
      todos: [
        { id: id++, text: "Lernas esperanto" },
        { id: id++, text: "Lernas ido" },
        { id: id++, text: "Lernas portugala" },
      ],
      todoId: 1,
      todoData: null,
    };
  },
  methods: {
    goup() {
      this.count++;
    },

    toggle() {
      this.awesome = !this.awesome;
    },

    addTodo() {
      this.todos.push({ id: id++, text: this.newTodo });
      this.newTodo = "";
    },
    removeTodo() {
      this.todos = this.todos.filter((t) => t !== todo);
    },
    removeTodo2() {
      this.todos.pop();
    },
    async fetchData() {
      this.todoData = null;
      const res = await fetch(
        `https://jsonplaceholder.typicode.com/todos/${this.todoId}`
      );
      this.todoData = await res.json();
    },
  },
  mounted() {
    setTimeout(() => {
      this.$refs.px.textContent = "mounted";
    }, 3000);

    this.fetchData();
  },
  watch: {
    todoId() {
      this.fetchData();
    },
  },
};
</script>

<style>
div {
  background-color: rgb(255, 234, 204);
  padding: 5px;
}

.vv {
  color: red;
}
</style>