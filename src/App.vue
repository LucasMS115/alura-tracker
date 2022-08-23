<template>
  <main class="columns is-gapless is-multiline" :class="{ 'dark-mode': isDarkModeActive }">
    <div class="column is-one-quarter">
      <SideBar @onChangeTheme="changeTheme"/>
    </div>
    <div class="column is-three-quarter content">
      <Formulary @onSaveTask="saveTask"/>
      <div class="task-list">
        <Task v-for="(task, index) in tasks" :key="index" :task="task"/>
        <Box v-if="isTaskListEmpty">
          Stop beeing lazy fella!
        </Box>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
  import { defineComponent } from 'vue';
  import SideBar from './components/SideBar.vue';
  import Formulary from './components/Formulary.vue';
  import Task from './components/Task.vue';
  import Box from './components/Box.vue';
  import ITask from './interfaces/ITask';

  export default defineComponent({
    name: 'App',
    components: {
      SideBar,
      Formulary,
      Task,
      Box
    },
    data () {
      return {
        tasks: [] as ITask[],
        isDarkModeActive: false
      }
    },
    computed: {
      isTaskListEmpty () : boolean {
        return this.tasks.length === 0
      }
    },
    methods: {
      saveTask (task: ITask) {
        this.tasks.push(task)
      },
      changeTheme (isDarkModeActive: boolean) {
        this.isDarkModeActive = isDarkModeActive
      }
    }
  });
</script>

<style>
  .task-list {
    padding: 1.25rem;
  }
  main {
    --background-primary: #fff;
    --text-primary: #000;
    --box-color: rgb(243, 247, 255);
  }
  main.dark-mode {
    --background-primary: #2b2d42;
    --text-primary: #ddd;
    --box-color: #181d3a;
  }
  .content {
    background-color: var(--background-primary);
  }
</style>
