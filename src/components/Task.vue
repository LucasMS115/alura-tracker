<template>
  <Box>
    <div class="columns">
      <div class="column is-7">{{ task.description || 'task without description' }}</div>
      <div class="column">
        <Chronometer :timeInSeconds="task.durationInSeconds"/>
      </div>
    </div>
  </Box>
</template>

<script lang="ts">
  import { defineComponent, PropType } from "vue";
  import Chronometer from "./Chronometer.vue";
  import ITask from '../interfaces/ITask'
  import Box from './Box.vue'

  export default defineComponent({
    name: "Task",
    components: {
      Chronometer,
      Box
    },
    props: {
      task: {
        type: Object as PropType<ITask>,
        required: true
      }
    }
  });
</script>
