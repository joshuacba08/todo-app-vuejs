<template>
    <div class="bg-slate-800 px-5 h-12 w-10/12 rounded-md mx-auto flex items-center gap-5">
        <div class="w-6 h-6 rounded-full border-[1px] border-slate-700"></div>
        <input  @change="handleChange" v-model="task" type="text" class="text-white">
    </div>
  
</template>

<script>
export default {
    data(){
        return{
            task:'',
        }
    },
    methods:{
        handleChange(e){
            this.$emit('sendTask',e)
            this.task = '';
        }
    }
}
</script>

<style>

</style>