<template>
    <ul v-if="tasks.length > 0">
        <li v-for="item in tasks" v-bind:key="item.description" class="text-white">{{item.description}}</li>
    </ul>
</template>

<script>
export default {
    props:{
        tasks: [Object],
    }
}
</script>

<style>

</style>