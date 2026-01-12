<template>
  <h1 class="text-white text-[2rem] mt-8 text-center">RSVP FORM</h1>
  <div>
    <base-card>
      <div class="flex justify-between items-center">
        <base-button @click="currentPage = 'the-form'">View Form</base-button>
        <base-button @click="currentPage = 'user-information'">View Data</base-button>
      </div>
    </base-card>

    <div>
        <component :is="currentPage"></component>
    </div>
  </div>
</template>

<script>
  import TheForm from './components/rsvp/TheForm.vue';
  import UserInformation from './components/rsvp/UserInformation.vue';


  export default {
    components: {
      TheForm,
      UserInformation,
    },
    data() {
      return{
        currentPage: 'TheForm',
      }
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
