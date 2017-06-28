<template>
  <div class='item'>
    <div class='buttons'>
      <button @click="$emit('delete')" class='del'>
        <i class="fa fa-trash" aria-hidden="true"></i>
      </button>
      <button @click="$emit('finish')" class='done'>
        <span v-if='item.finished'>
          <i class="fa fa-undo" aria-hidden="true"></i>
        </span>
        <span v-else>
          <i class="fa fa-check" aria-hidden="true"></i>
        </span>
      </button>
    </div>
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


<!--✔-->