<template>
  <div id="container">
    <h1>{{ msg }}</h1>
    <input
      v-model="inputText"
      placeholder="Enter new task"
      @keydown.enter="addTask"
    />
    <button @click="hideTasks">{{ hidden ? "Show" : "Hide" }} Tasks</button>
    <ul v-show="hidden === false">
      <TodoItem
        v-for="(task, index) in tasks"
        :key="task.id"
        :title="task.title"
        :is-finished="task.isFinished"
        @remove-item="removeTask(index)"
      ></TodoItem>
    </ul>
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";

export default {
  name: "HelloWorld",
  components: {
    TodoItem,
  },
  data() {
    return {
      tasks: [],
      inputText: "",
      hidden: false,
    };
  },
  props: {
    msg: String,
  },
  methods: {
    addTask() {
      if (this.inputText !== "") {
        this.tasks.push({title: this.inputText, isFinished: false, id: Math.random()});
      } else {
        return;
      }
      this.inputText = "";
    },
    removeTask(idx) {
      this.tasks.splice(idx, 1);
    },
    hideTasks() {
      this.hidden = !this.hidden;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#container {
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
#container ul {
  list-style: none;
  margin: 1rem 0;
  padding: 0;
  overflow: auto;
  max-height: 10rem;
}
#container input {
  width: 90%;
  padding: 0px;
  font-size: 1.25rem;
  border-radius: 1rem;
  border-style: solid;
  padding: 0.4rem;
  margin-bottom: 15px;
}
#container button {
  font: inherit;
  cursor: pointer;
  border: none;
  background-color: #ff0077d7;
  border-radius: 1rem;
  color: white;
  padding: 0.2rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}

</style>
