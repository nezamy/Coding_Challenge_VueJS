<template lang="html">
  <div>
    <v-list-tile @click="update({completed: !completed})">
    
      <v-list-tile-action>
        <v-icon :color="completed ? 'green accent-4' : 'grey'">{{ completed ? 'done' : 'check_box_outline_blank' }}</v-icon>
      </v-list-tile-action>

      <v-list-tile-content>
        <v-list-tile-title
          :class="completed ? 'complete-task' : ''" 
          v-text="title" />
      </v-list-tile-content>

      <v-list-tile-action>
        <v-btn 
          color="error"
          small
          flat
          icon
          @click="remove(id)">
          <v-icon color="red">delete</v-icon>
        </v-btn>
      </v-list-tile-action>

    </v-list-tile>
    <v-divider />
  </div>
</template>

<script>
import VueTypes from 'vue-types'
export default {
  props: {
    id: VueTypes.string.required,
    title: VueTypes.string.required,
    completed: VueTypes.bool.required,

  },
  methods: {
    update(task){
      this.$emit('update', {
        ...task,
        id: this.id 
      });
    },
    remove(id){
      this.$emit('remove', id);
    }
  }
}
</script>

<style lang="css">
.complete-task{
  text-decoration: line-through;
  color: gray;
}
</style>
