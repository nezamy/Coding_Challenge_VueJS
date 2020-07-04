<template lang="html">
  <div>
    
    <v-list subheader>
      <v-subheader>You have {{ tasks.length }} task to do</v-subheader>
      <TodoItem 
        v-if="tasks"
        v-for="task in tasks" 
        :key="task.id"
        :id="task.id" 
        :title="task.title"
        :completed="task.completed"
        @update="update"
        @remove="remove"
      />
      <v-divider />
  
    </v-list>
  </div>
</template>

<script>
import TodoItem from '@/components/todo-item';
import VueTypes from 'vue-types'

export default {
  props: {
    tasks: VueTypes.array.required,
  },
  components: {
    TodoItem,
  },
  methods: {
    update(task){
      this.$emit('update', task);
    },
    remove(id){
      this.$emit('remove', id);
    }
  }
}
</script>

<style lang="css">
</style>
