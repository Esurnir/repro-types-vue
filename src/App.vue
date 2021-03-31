<template>
  <div id="app">
    <my-component-1 id="1" />
    <my-component-2 id="2" />
  </div>
</template>

<script lang="ts">
import Vue, { AsyncComponent } from 'vue';
import Loading from './components/Loading.vue';

const MyComponent1: AsyncComponent = () => ({
  component: () => import('./components/MyComponent.vue'),
  loading: Loading,
});

const MyComponent2: AsyncComponent = () => ({
  // @ts-expect-error Ceci n'est pas une factory qui retourne la fonction mais la promesse réel
  component: import('./components/MyComponent.vue'),
  loading: Loading,
});

export default Vue.extend({
  name: 'App',
  components: {
    MyComponent1,
    MyComponent2,
  },
});
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
</style>
