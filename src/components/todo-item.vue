<template>
  <div class='item'>
    <button @click="$emit('delete')" class='del'>X</button>
    <!--<button @click="$emit('finish')">✔</button>-->
    <span v-bind:class="{finished: item.finished}">{{item.name}}</span>
  </div>
</template>

<script>
  export default {
    props: {
        item: Object
      }
    }
</script>