<template>
  <div id="app">
    <Calc></Calc>
  </div>
</template>

<script>
import "./scss/app.scss";
import Calc from './components/Calc.vue'

export default {
  name: 'App',
  components: {
    Calc
  }
}
</script>
