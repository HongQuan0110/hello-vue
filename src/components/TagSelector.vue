<template>
    <div class="tag-selector">
        <div v-for="(language, index) in languages" :key="index" @click="language.selected = !language.selected" :class="{selected: language.selected}">
            {{ language.name }}
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            languages: [
                { name: 'php', selected: false },
                { name: 'html', selected: false },
                { name: 'css', selected: false },
                { name: 'javscript', selected: false },
                { name: 'nodejs', selected: false }
            ]
        }
    }
}
</script>

<style scoped>
.tag-selector div {
    display: inline-block;
    padding: 4px 15px;
    border: 1px solid #ebebeb;
    border-radius: 4px;
    margin-left: 5px;
    cursor: pointer;
}
.tag-selector {
    text-align: left;
}

.tag-selector .selected {
    background-color: green;
    color: white;
}
</style>
