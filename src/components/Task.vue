<template>
    <div class="task">
        <input type="checkbox" name="" id="" v-model="taskData.done">  
        <span :class="{complete: taskData.done}">{{ taskData.content }}</span>
    </div>
</template>

<script>
export default {
    // Du lieu lay tu component cha => con
    // Dung mang ten cac props hoac object key la cac prop
    // Prop cung giong nhu data
    props: {
        taskData: Object
    },
    data() {
        return {

        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
