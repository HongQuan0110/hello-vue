<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Menu />

    <!-- Conditional rendering -->
    <!-- 
      + v-show: an/hien element theo dieu kien
      + v-hide: ngc lai
      + v-if: bien mat/hien thi element theo dieu kien
      + v-elseif
      + v-else
     -->
    <input type="text" v-model="name" />
    <div v-show="isShow">
      {{name}}
    </div>
    <button @click="() => isShow = !isShow">
      <!-- {{isShow ? 'Ẩn' : 'Hiện'}} -->
      <span v-if="!isShow">Hiện</span>
      <span v-else>Ẩn</span>
    </button>

    <!-- Binding value/property/style/class -->
    <!-- 
      + v-binding:[tenthuoctinh]="bien"
      + viet tat : dau 2 cham 
    -->
    <div>
      <input type="text" v-bind:disabled="isDisable" />
      <button @click="isDisable = !isDisable">Mo/Khoa</button>
    </div>
    
    <h1 :class="{colorRed: selected}">Binding class</h1>
    <button @click="() => selected = !selected">Click</button>

    <!-- Event Handler -->
    <!-- 
      + v-on:[tensukien]="function()"
      + v-on viet tat @ 
      + prevent default event:
        + huy bo event mac dinh cua element
    -->
    <div>
      <input type="text" v-model="chanel.name">
      <button v-on:mouseover="chanel.name = 'XYZ'">Click</button>
      <form action="/abc">
        <input type="submit" @click.prevent="chanel.name = 'DEF'">
      </form>
    </div>

    <!-- ref: Anh xa den chinh elemen - this.$ref.[ten] -->
    <h2 ref="text">ref</h2>

    <!-- List rendering -->
    <!-- 
      + v-for
     -->
    <div>
      <input type="text" v-model="newTask">
      <button @click="addTask" >Add</button>
      <task v-for="(task, index) in tasks" :key="index" :taskData="task"/>
    </div>

    <TagSelector />
  </div>
</template>

<script>

import Menu from './components/Menu.vue'
import Task from './components/Task.vue'
import TagSelector from './components/TagSelector.vue'

export default {
  name: 'App',
  data() {
    return {
      name: "Vue",
      isShow: true,
      isDisable: true,
      selected: false,
      chanel: {
        name: 'ABC'
      },
      tasks: [
        {content:'di lam', done: false},
        {content:'tap gym', done: false},
        {content:'choi game', done: false},
        {content:'an toi', done: false},
      ],
      newTask: ''
    }
  },
  components: {
    Menu,
    Task,
    TagSelector
  },
  // Ham cua vue object
  methods: {
    addTask: function() {
      this.tasks.push({
        content: this.newTask,
        done: false
      })
    }
  },
  // Theo doi su thay doi cua data, ten dat giong bien
  watch: {
    newTask: function(newValue, oldValue) {
      console.log("watch: ", this.tasks)
      console.log("watch: ", oldValue)
      console.log("watch: ", newValue)
    }
  },
  mounted() {
    console.log(this.$refs.text)
  },
  updated() {
    console.log("updated: ", this.newTask)
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.colorRed {
  color: red;
}

.complete {
  text-decoration: line-through;
}
</style>
