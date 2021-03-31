<template>
  <p>Loaded ! id {{ id }}</p>
</template>
<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  props: ['id'],
});
</script>
