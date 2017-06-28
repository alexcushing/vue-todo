<template>
  <div id="app">

    <h1>To Do List</h1>

    <form v-on:submit="addToDo" class='form'>
      <input v-model="current">
      <button type="submit" class='add'>+</button>
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
        this.list.push({name: item, finished: false})
        this.current = ''
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

<!-- CSS libraries -->
<style src="normalize.css/normalize.css"></style>


<style>
@import url('https://fonts.googleapis.com/css?family=Arvo');
*:focus {
    outline: none;
}
body{
  box-sizing: border-box;
  font-family: 'Arvo', serif;
}

#app {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.add {
  padding: 3px;
  font-size: 12px;
  font-weight: bolder;
  background: white;
  border: solid 1px black;
  border-left: none;
  margin-left: 0px;
  color: green;
}

input {
  padding: 3px;
  font-size: 12px;
  background: white;
  border: solid 1px black;
  border-right: none;
  margin-right: 0px;
}

.add:focus {
  outline: none;
  border-left: none;
}

.items {
  overflow-x: hidden;
  white-space: nowrap;
  text-overflow: ellipses;
  width: 400px;
  margin: 15px;
  display: flex;
  flex-direction: column;
  align-items: flex-end;
}

.item {
  padding: 10px;
  width: 390px;
  display: flex;
  justify-content: space-between;
}

.del {
  color: red;
  cursor: pointer;
  background: none;
  border: none;
  font-size: 12px;
}

.form {
  display: flex;
  justify-content: center;
}

.finished {
  text-decoration: line-through;
}

</style>