<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <Chronometer :timeInSeconds="timeInSeconds" />

    <button class="button" @click="start" :disabled="isChronometerRunning">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>Play</span>
    </button>

    <button class="button" @click="finish" :disabled="!isChronometerRunning">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>Stop</span>
    </button>

  </div>
</template>

<script lang="ts">
  import { defineComponent } from "vue";
  import Chronometer from './Chronometer.vue'

  export default defineComponent({
    name: "Timer",
    emits: ['onFinishTimer'],
    components: {
      Chronometer
    },
    data () {
      return {
        timeInSeconds: 0,
        Chronometer: 0,
        isChronometerRunning: false
      }
    },
    methods: {
      start () {
        this.isChronometerRunning = true;

        this.Chronometer = setInterval(() => {
          this.timeInSeconds += 1;
        }, 1000)
      },
      finish () {
        this.isChronometerRunning = false;
        clearInterval(this.Chronometer);
        this.$emit('onFinishTimer', this.timeInSeconds);
        this.timeInSeconds = 0;
      }
    }
  });
</script>