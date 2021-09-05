<template>
  <v-app>
    <v-main style="width: 100%">
      <Navigation/>
      <router-view class="page" />
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
