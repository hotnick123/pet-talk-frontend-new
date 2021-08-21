<template>
  <v-app>
    <v-main>
      <Navigation/>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>
// import HelloWorld from './components/HelloWorld';
import Navigation from './components/Navigation.vue';

export default {
  name: 'App',

  components: {
    Navigation,
    // HelloWorld,
  },

  data: () => ({
    //
  }),
};
</script>
