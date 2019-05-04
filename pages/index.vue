<template>
  <GridContainer direction="column" alignX="center" alignY="center">
    <StyledTitle
      :styles="{ marginTop: '40px' }"
      title="SpaceX SSR" />
    <StyledSubTitle
      :styles="{ marginBottom: '40px' }"
      text="Rockets are amazing!"/>

    <RocketList
      :rockets="rockets"
    />
  </GridContainer>
</template>

<script>
import StyledTitle from '@/components/Functional/StyledTitle';
import StyledSubTitle from '@/components/Functional/StyledSubTitle';
import GridContainer from '@/components/Functional/GridContainer';
import RocketList from '@/components/RocketList';

export default {
  name: 'Index',
  components: {
    StyledTitle,
    StyledSubTitle,
    GridContainer,
    RocketList,
  },
  async asyncData({ $axios }) {
    const rockets = await $axios.$get('/rockets');
    return { rockets };
  },
}
</script>
