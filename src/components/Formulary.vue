<template>
  <div class="box form-container">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Form to create new task"
      >
        <input
          type="text"
          class="input"
          placeholder="What r u going to do?"
          v-model="description"
        />
      </div>
      <div class="column">
        <Timer @onFinishTimer="finishTask"/>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
  import { defineComponent } from "vue";
  import Timer from './Timer.vue';

  export default defineComponent({
    name: "Formulary",
    emits: ['onSaveTask'],
    components: {
      Timer
    },
    data () {
      return {
        description: ''
      }
    },
    methods: {
      finishTask (elapsedTime: number) : void {
        this.$emit('onSaveTask', {
          durationInSeconds: elapsedTime,
          description: this.description
        });

        this.description = '';
      }
    }
  });
</script>

<style>
  .form-container {
    color: var(--text-primary);
    background-color: var(--background-primary);
  }
</style>