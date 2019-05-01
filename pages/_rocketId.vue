<template>
  <GridContainer direction="column">
    <RocketCard
      fluid
      :key="`rocket-${index}`"
      :rocket="rocket"
    />
    <GridContainer
      :styles="{ padding: '5px 30px 30px 30px' }">
      <StyledDescription>
        {{ rocket.description }}
      </StyledDescription>
    </GridContainer>
  </GridContainer>
</template>

<script>
import StyledTitle from '@/components/Functional/StyledTitle';
import StyledSubTitle from '@/components/Functional/StyledSubTitle';
import StyledDescription from '@/components/Functional/StyledDescription';
import GridContainer from '@/components/Functional/GridContainer';
import RocketCard from '@/components/RocketCard';

export default {
  name: 'Index',
  components: {
    StyledTitle,
    StyledSubTitle,
    StyledDescription,
    GridContainer,
    RocketCard,
  },
  async asyncData({ $axios, route }) {
    const rocket = await $axios.$get('/rockets/' + route.params.rocketId);
    return { rocket };
  },
}
</script>

<style>

</style>
