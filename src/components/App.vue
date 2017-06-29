<template>
  <div id="app">

    <h1>To Do List</h1>

    <form v-on:submit="addToDo" class='form'>
      <input v-model="current">
      <button type="submit" class='add'><i class="fa fa-plus" aria-hidden="true"> </i></button>
    </form>
    <div class='items'>
      <div v-for="item in list">
        <todo-item v-bind:item="item" @delete="deleteToDo(item)" @finish="finishToDo(item)"></todo-item>
      </div>
    </div>


  </div>
</template>

<script>
import TodoItem from './todo-item.vue';
  export default {
    name: 'app',
    data () {
    return {
      current: "",
      list : []
    }
    },
    components: { TodoItem },
    methods: {
      addToDo(e) {
        e.preventDefault();
        let item = this.current
        if (item.trim() != '') {

        this.list.push({name: item, finished: false})
        this.current = ''
        }
      },
      deleteToDo(item) {
        var index = this.list.indexOf(item);
        this.list.splice(index,1)
      },
      finishToDo(item) {
        item.finished ? item.finished = false : item.finished = true;
      }
    }
  }
</script>