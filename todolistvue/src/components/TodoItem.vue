<template>
  <li class="container__item" :class="{ 'container__item--finished': taskIsFinished }">
    <button class="gg-close-o" @click="removeItem"></button>
    <button class="gg-check-o" @click="finishTask"></button>
    {{ title }}
  </li>
</template>

<script>
export default {
  props: {
    title: String,
    id: Number,
    isFinished: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      taskIsFinished: this.isFinished,
    };
  },
  methods: {
    finishTask() {
      this.taskIsFinished = !this.taskIsFinished;
    },
    removeItem() {
      this.$emit("remove-item");
    },
  },
};
</script>

<style scoped>
.container__item {
  margin: 1rem 0;
  font-size: 1.25rem;
  font-weight: bold;
  text-align: center;
  background-color: rgba(155, 223, 255, 0.836);
  box-shadow: 0 0 0.5rem rgb(0 0 0 / 10%);
  padding: 0.5rem;
  color: #1f1f1f;
  border-radius: 1rem;
  word-wrap: break-word;
}
.container__item--finished {
  text-decoration: line-through;
  opacity: 0.6;
  background-color: rgba(158, 255, 155, 0.836);
}

.gg-close-o {
  box-sizing: border-box;
  position: relative;
  display: block;
  transform: scale(var(--ggs, 1));
  width: 22px;
  height: 22px;
  border: 2px solid;
  border-radius: 40px;
  background-color: rgba(155, 223, 255, 0);
  float: right;
  cursor: pointer;
}
.gg-close-o::after,
.gg-close-o::before {
  content: "";
  display: block;
  box-sizing: border-box;
  position: absolute;
  width: 12px;
  height: 2px;
  background: currentColor;
  transform: rotate(45deg);
  border-radius: 5px;
  top: 8px;
  left: 3px;
}
.gg-close-o::after {
  transform: rotate(-45deg);
}
.gg-close-o:hover {
  color: red;
}
.gg-check-o {
  box-sizing: border-box;
  position: relative;
  display: block;
  transform: scale(var(--ggs, 1));
  width: 22px;
  height: 22px;
  border: 2px solid;
  border-radius: 100px;
  background-color: rgba(155, 223, 255, 0);
  float: left;
  cursor: pointer;
}
.gg-check-o::after {
  content: "";
  display: block;
  box-sizing: border-box;
  position: absolute;
  left: 3px;
  top: -1px;
  width: 6px;
  height: 10px;
  border-color: currentColor;
  border-width: 0 2px 2px 0;
  border-style: solid;
  transform-origin: bottom left;
  transform: rotate(45deg);
}
.gg-check-o:hover {
    color: green;
}
</style>
