<template>
  <div id="app">
    <h1>My users</h1>
    <UsersList>
      <!-- <template v-slot:title="{user}">
        <span v-if="user">{{user.name.last}}  {{user.name.first}}</span>
      </template> -->
     <!--  <template v-slot:subtitle="{user}">
        <span v-if="user">FER</span>
      </template> -->
     <!--  <template v-slot:address="{user}">
        <span v-if="user">DIRECCIÓN</span>
      </template> -->
    </UsersList>
  </div>
</template>

<script>

import UsersList from './components/UsersList';

export default {
  name: 'app',
  components: {
    UsersList 
  }
};
</script>

<style lang="scss">
 @import url("https://fonts.googleapis.com/css?family=Oxygen:400,700,300");
      @import url("https://maxcdn.bootstrapcdn.com/font-awesome/4.3.0/css/font-awesome.min.css");
     
      *, *:after, *:before {
        box-sizing: border-box;
      }
     
      body {
        background: #FAFAFA;
        color: #3F3F3F;
        padding: 1em;
        font-size: 62.5%;
        -webkit-font-smoothing: antialiased;
        font-family: 'Oxygen', Helvetica, sans-serif;
      }
     
      h1 {
        text-align: center;
        text-line-height: 1.5;
        margin: auto;
        font-size: 1.5rem;
      }

</style>
