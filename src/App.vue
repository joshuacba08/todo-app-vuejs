<template>
  <div class="w-screen h-screen bg-slate-900">
    <Header />
    <TaskContainer />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import TaskContainer from "./components/TaskContainer.vue";

export default {
  name: "App",
  components: {
    Header,
    TaskContainer
},
};
</script>

<style></style>


<!-- 
Todo
items left All Active Completed Clear Completed Drag and drop to reorder list

<div class="attribution">
  Challenge by
  <a href="https://www.frontendmentor.io?ref=challenge" target="_blank"
    >Frontend Mentor</a
  >. Coded by <a href="#">Your Name Here</a>.
</div> -->
