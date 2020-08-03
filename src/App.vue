<template>
  <div id="app">
    <Calc :res="result" @result="this.result = res"></Calc>
  </div>
</template>

<script>
import "./scss/app.scss";
import Calc from './components/Calc.vue'

export default {
  name: 'App',
  data(){
    return{
      result = '0',
      number = [],
      operations = []
    }
  },
  components: {
    Calc
  }
}
</script>
