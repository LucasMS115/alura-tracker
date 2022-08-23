<template>
  <header>
      <h1>
        <img src="../assets/logo.png" alt="">
      </h1>
      <button class="button" @click="changeTheme">
        {{ textoBotao }}
      </button>
  </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'SideBar',
  emits: ['onChangeTheme'],
  data () {
    return {
      isDarkModeActive: false
    }
  },
  computed: {
    textoBotao () {
      if (this.isDarkModeActive) {
        return 'Deactivate dark mode';
      }
      return 'Activate dark mode';
    }
  },
  methods: {
    changeTheme () {
      this.isDarkModeActive = !this.isDarkModeActive;
      this.$emit('onChangeTheme', this.isDarkModeActive);
    }
  }
})
</script>

<style scoped>
  header {
    padding: 1rem;
    background: #0d3b66;
    width: 100%;
    height: 100vh;
    text-align: center;
  }

  @media only screen and (max-width: 768px) {
    header {
      padding: 2.5rem;
      height: auto;
    }
  }
</style>
