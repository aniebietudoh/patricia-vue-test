<template>
  <div class="home">
    <CardComponent />
  </div>
</template>

<script>
// @ is an alias to /src
import CardComponent from '@/components/CardComponent.vue';

export default {
  name: 'Home',
  components: {
    CardComponent,
  },
};
</script>
