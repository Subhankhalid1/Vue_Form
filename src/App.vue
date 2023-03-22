<template>
 <h3>Form</h3>
 <SignUpForm/>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import SignUpForm from './components/Form/SignUpForm.vue';
export default {
  name: 'App',
  components: {
    SignUpForm
 
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body{
  background: #eee;
  margin: 0;
}
</style>
