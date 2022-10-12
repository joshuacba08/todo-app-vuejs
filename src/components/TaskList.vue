<template>
  <ul
    v-if="tasks.length > 0"
    class="w-10/12 mt-5 rounded-lg mx-auto flex items-center gap-[1px] flex-col overflow-hidden"
  >
    <li
      v-for="item in tasks"
      v-bind:key="item.id"
      class="flex items-center h-12 gap-5 text-white bg-slate-800 w-full px-5"
    >
      <button
        v-on:click="changeState(item.id)"
        class="flex justify-center items-center w-6 h-6 rounded-full border-[1px] border-slate-700"
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
      {{ item.description }}
    </li>
    <li
      class="flex items-center justify-between h-12 bg-slate-800 w-full px-5 font-semibold text-slate-500"
    >
      <span>5 items left</span>
      <button>Clear Completed</button>
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
    }
  }
};
</script>

<style></style>
