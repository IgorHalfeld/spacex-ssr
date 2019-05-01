<template>
  <div>
    <RocketCard
      v-for="(rocket, index) in rockets"
      :key="`rocket-${index}`"
      :rocket="rocket"
    />
  </div>
</template>

<script>
import RocketCard from '@/components/RocketCard';

export default {
  name: 'RocketList',
  components: { RocketCard },
  props: {
    rockets: { type: Array, required: true },
  },
};
</script>

<style>

</style>
