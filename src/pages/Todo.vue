<template>
  <q-page class="bg-grey-3 column">
    <div class="row q-pa-sm bg-primary">
      <q-input
      v-model="newTask"
      @keyup.enter = "addTask"
      class="col"
      square
      filled
      bg-color="white"
      placeholder="Add task"
      dense>
        <template v-slot:append>
          <q-btn
          @click="addTask"
          round
          dense
          flat
          icon="add" />
        </template>
      </q-input>

    </div>
    <q-list class="bg-white"
    separator bordered>
      <q-item
      v-for="(task, index) in tasks"
      :key="task.title"
      @click="task.done = !task.done"
      :class="{ 'done bg-blue-1' : task.done }"
      clickable
      v-ripple>
        <q-item-section avatar>
          <q-checkbox v-model="task.done"
          class="no-pointer-events"
          color="primary" />
        </q-item-section>
        <q-item-section>
          <q-item-label>{{ task.title }}</q-item-label>
        </q-item-section>
        <q-item-section
          v-if="task.done"
          side>
          <q-btn
            @click.stop="deleteTask(index)"
            flat
            round
            dense
            color="primary"
            icon="delete" />
        </q-item-section>
        </q-item-section>
      </q-item>
    </q-list>
    <div
    v-if="!tasks.length"
    class="no-task absolute-center">
     <q-icon
      name= "check"
      size= "100px"
      color= "primary" />
      <div class="text-h5 text-primary text-center">
        No tasks
      </div>
    </div>
  </q-page>
</template>

<script>
export default {
  data () {
    return {
      newTask: '',
      tasks: [
        {
          title: 'Wake up',
          done: true
        },
        {
          title: 'Write code',
          done: true
        },
        {
          title: 'Get a job',
          done: false
        } 
      ]
    }
  },
  methods: {
    deleteTask (index) {
      this.$q.dialog({
        title: 'Confirm',
        message: 'Really delete?',
        cancel: true,
        persistent: true
      }).onOk(() => {
        this.tasks.splice(index, 1)
        this.$q.notify('Task deleted')
      })
    },
    addTask () {
      this.tasks.push({
        title: this.newTask,
        done: false,
        editing: false
      })
      this.newTask = ''
    },
        editTodo(index) {
      this.beforeEditCache = index.title
      index.editing = true
    },
    doneEdit(index) {
      if (index.title.trim() == '') {
        index.title = this.beforeEditCache
      }
      index.editing = false
    },
    cancelEdit(index) {
      index.title = this.beforeEditCache
      index.editing = false
    }
  }
}
</script>
<style lang="scss">
  .done {
    .q-item__label {
      text-decoration: line-through;
      color: #bbb;
    }
  }
</style>
