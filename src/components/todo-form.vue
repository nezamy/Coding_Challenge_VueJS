<template lang="html">
  <v-text-field
    label="Todo"
    placeholder="What do you have to do?"
    solo
    @keydown.enter="add"
    v-model="task"
  />
</template>

<script>
// import VueTypes from 'vue-types'

export default {
  data(){
    return {
      task: ''
    }

  },
  methods: {
    add(){
      this.$emit('add', this.task);
      this.task = '';
    }
  },
}
</script>

<style lang="css">
</style>
