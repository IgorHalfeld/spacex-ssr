<template>
  <GridContainer direction="column" alignY="center">
    <RocketCard
      fluid
      :rocket="rocket"
    />
    <GridContainer
      :styles="{ padding: '5px 30px 30px 30px', maxWidth: '800px' }"
      direction="column">
      <StyledDescription>
        {{ rocket.description }}
      </StyledDescription>
      <GridContainer
        :styles="{ width: '100%', marginTop: '20px' }"
        alignX="center">
        <StyledList :items="specs" />
      </GridContainer>
    </GridContainer>
  </GridContainer>
</template>

<script>
import StyledTitle from '@/components/Functional/StyledTitle';
import StyledSubTitle from '@/components/Functional/StyledSubTitle';
import StyledDescription from '@/components/Functional/StyledDescription';
import GridContainer from '@/components/Functional/GridContainer';
import StyledList from '@/components/Functional/StyledList';
import RocketCard from '@/components/RocketCard';

export default {
  name: 'Index',
  components: {
    StyledTitle,
    StyledSubTitle,
    StyledDescription,
    GridContainer,
    RocketCard,
    StyledList,
  },
  async asyncData({ $axios, route }) {
    const rocket = await $axios.$get('/rockets/' + route.params.rocketId);
    const specs = [
      { emoji: '🚀' , label: rocket.first_flight },
      { emoji: '📐', label: `${rocket.height.meters} meters`},
      { emoji: '🐳', label: `${rocket.mass.kg} kg`},
    ];

    return { rocket, specs };
  },
}
</script>

<style>

</style>
