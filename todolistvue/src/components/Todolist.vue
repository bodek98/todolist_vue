<template>
  <div id="container">
    <h1>{{ msg }}</h1>
    <p>Input your task</p>

    <input
      v-model="inputText"
      placeholder="Enter new task"
      @keydown.enter="addTask"
    />
    <button @click="hideTasks">{{ hidden ? "Show" : "Hide" }} Tasks</button>
    <ul v-if="hidden === false">
      <li
        v-for="(task, index) in tasks"
        :key="index"
        :class="{finished__task: finished}"
      >
      {{ task }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      inputText: "",
      tasks: [],
      hidden: false,
      finished: false,
      index: 0
    };
  },
  props: {
    msg: String,
  },
  methods: {
    addTask() {
      if (this.inputText !== "") {
        this.tasks.push(this.inputText);
      } else {
        alert("Please input something :)");
      }
      this.inputText = "";
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
  width: 24rem;
  border-radius: 1rem;
  box-shadow: 0 0 1rem rgb(0 0 0 / 50%);
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
}
#container li {
  margin: 1rem 0;
  font-size: 1.25rem;
  font-weight: bold;
  background-color: rgb(164, 255, 155);
  border: solid 0.2px;
  padding: 0.5rem;
  color: #1f1f1f;
  border-radius: 25px;
  cursor: pointer;
}
.finished__task {
  text-decoration: line-through;
  background-color: #1f1f1f;
}
#container button {
  font: inherit;
  cursor: pointer;
  border: 2px solid #9b2164;
  background-color: #ff0077;
  border-radius: 1rem;
  color: white;
  padding: 0.2rem 1rem;
  margin-top: 10px;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}
#container input {
  width: 90%;
  padding: 0px;
  font-size: 1.25rem;
  border-radius: 1rem;
  border-style: solid;
  padding: 0.4rem;
}

</style>
