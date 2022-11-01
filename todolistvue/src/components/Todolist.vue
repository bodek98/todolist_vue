<template>
  <div class="container">
    <h1>{{ title }}</h1>
    <input
      class="container__input"
      v-model="inputText"
      placeholder="Enter new task"
      @keydown.enter="addTask"
    />
    <ul class="container__ul" v-show="!hidden">
      <TodoItem
        v-for="task in tasks"
        :key="task.id"
        :title="task.title"
        :is-finished="task.isFinished"
        @remove-item="removeTask(task.id)"
      ></TodoItem>
    </ul>
    <button class="container__button" @click="hideTasks">
      {{ hidden ? "Show" : "Hide" }} Tasks
    </button>
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";

export default {
  name: "todoList",
  components: {
    TodoItem,
  },
  data() {
    return {
      tasks: [],
      inputText: "",
      taskId: 1,
      hidden: false,
    };
  },
  props: {
    title: String,
  },
  methods: {
    addTask() {
      if (this.inputText !== "") {
        this.tasks.push({
          title: this.inputText,
          isFinished: false,
          id: this.taskId,
        });
      } else {
        return;
      }
      this.taskId++;
      this.inputText = "";
    },
    removeTask(idx) {
      let i = this.tasks.map((task) => task.id).indexOf(idx);
      this.tasks.splice(i, 1);
    },
    hideTasks() {
      this.hidden = !this.hidden;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  font-size: 1.25rem;
  background-color: white;
  width: 26rem;
  border-radius: 1rem;
  box-shadow: 0 0 2rem rgb(0 0 0 / 50%);
  padding: 10px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.container__ul {
  list-style: none;
  margin: 0;
  padding: 0;
  overflow: auto;
  max-height: 10rem;
}
.container__input {
  width: 90%;
  padding: 0px;
  font-size: 1.25rem;
  border-radius: 1rem;
  border-style: solid;
  padding: 0.4rem;
  margin-bottom: 10px;
}
.container__button {
  font: inherit;
  cursor: pointer;
  border: none;
  background-color: #ff0077d7;
  border-radius: 1rem;
  color: white;
  padding: 0.2rem 1rem;
  box-shadow: 1px 1px 2px rgb(0, 0, 0);
  margin-top: 10px;
}
.container__button:hover {
  background-color: #ee0066c6;
}
</style>
