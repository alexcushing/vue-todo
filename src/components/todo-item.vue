<template>
  <div class='item'>
    <div class='buttons'>
      <button @click="$emit('delete')" class='del'>
        <i class="fa fa-trash-o" aria-hidden="true"></i>
      </button>
      <button @click="$emit('finish')" class='done'>
        <span v-if='item.finished' class='undo'>
          <i class="fa fa-undo" aria-hidden="true"></i>
        </span>
        <span v-else>
          <i class="fa fa-check" aria-hidden="true"></i>
        </span>
      </button>
    </div>
    <input v-bind:class="{finished: item.finished}" v-model="item.name" class='edit-input'>
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