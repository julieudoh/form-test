<template>
  <h1 class="text-white text-[2rem] mt-8 text-center">RSVP FORM</h1>
  <the-form></the-form>
</template>

<script>
  import TheForm from './components/rsvp/TheForm.vue';


  export default {
    components: {
      TheForm
    }
  }
</script>


<style scope>
  *{
    box-shadow: border-box;
  }
  html{
    font-family: sans-serif;
  }
  body{
    margin: 0;
    background-color: rgb(3, 33, 73);
  }
</style>
