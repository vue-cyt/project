<template>
  <div>
    <div>
      <input v-model='inputValue' />
      <button @click="handleClick">提交</button>
    </div>
    <ul>
      <todo-item
        v-for="(item, index) of list"
        :key="index"
        :content="item"
        :index="index"
        @delete="handleDelete($event)"
      ></todo-item>
    </ul>
    <router-link to="/">1111</router-link>
  </div>
</template>

<script>
import TodoItem from "./components/TodoItem";

export default {
  name: "App",
  data() {
    return {
      inputValue: "",
      list: [],
    };
  },
  components: {
    "todo-item": TodoItem,
  },
  methods: {
    handleClick() {
      this.list.push(this.inputValue);
      this.inputValue = "";
    },
    handleDelete(index) {
      this.list.splice(index, 1);
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
