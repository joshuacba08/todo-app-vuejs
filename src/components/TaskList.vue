<template>
  <ul
    v-if="tasks.length > 0"
    class="w-10/12 mt-5 rounded-lg mx-auto flex items-center gap-[1px] flex-col overflow-hidden"
  >
    <li
      v-for="item in tasks"
      v-bind:key="item.id"
      :class="`flex items-center justify-between h-12 gap-5 text-white bg-slate-800 w-full px-5 ${ item.state ? 'line-through' : null }`"
    >
      <button
        v-on:click="changeState(item.id)"
        :class="`flex justify-center items-center w-6 h-6 rounded-full border-[1px] border-slate-700 ${ item.state ? 'bg-gradient-to-r from-sky-500 to-fuchsia-500' :'null' }`"
      >
        <svg v-if="item.state" xmlns="http://www.w3.org/2000/svg" width="11" height="9">
          <path
            fill="none"
            stroke="#FFF"
            stroke-width="2"
            d="M1 4.304L3.696 7l6-6"
          />
        </svg>
      </button>
      <p class="w-3/4">{{ item.description }}</p>

      <svg v-on:click="deleteTask(item.id)" xmlns="http://www.w3.org/2000/svg" width="18" height="18"><path fill="#494C6B" fill-rule="evenodd" d="M16.97 0l.708.707L9.546 8.84l8.132 8.132-.707.707-8.132-8.132-8.132 8.132L0 16.97l8.132-8.132L0 .707.707 0 8.84 8.132 16.971 0z"/></svg>
    </li>
    <li
      class="flex items-center justify-between h-12 bg-slate-800 w-full px-5 font-semibold text-slate-500"
    >
      <span>{{ getTaskLeft() }} items left</span>
      <button v-on:click="clearCompleteTasks()">Clear Completed</button>
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    tasks: [Object],
  },
  methods:{
    changeState(id){
        console.log('id: ',id);
        this.$emit('changeState',id)
    },
    getTaskLeft(){
      const result = this.tasks.filter( task => task.state === false );
      return result.length;
    },
    clearCompleteTasks(){
      console.warn('limpiando tareas...');
      this.$emit('clearComplete');
    },
    deleteTask(id){
      this.$emit('deleteTask',id)
    }
  }
};
</script>

<style></style>
