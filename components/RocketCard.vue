<template>
  <div
    @click="() => $router.push(`/${rocket.rocket_id}`)"
    :style="{
      width: fluid ? '100vw' : '600px',
      height: fluid ? '500px': '400px',
      backgroundImage: `url(${rocket.flickr_images[0]})`,
      backgroundPosition: fluid ? '40% 40%' : 'center center'
    }"
    class="card">
    <span
      :style="{
        width: fluid ? '100vw' : '600px',
        height: fluid ? '500px': '400px',
      }"
      class="card-overlay"></span>
    <GridContainer
      :styles="{
        height: '100%',
        padding: '30px',
      }"
      direction="column"
      :alignY="fluid ? 'center' : 'flex-start'"
      alignX="flex-end">
      <StyledTitle
        :styles="{
          color: 'white',
          zIndex: 2,
        }"
        :title="rocket.rocket_name" />
      <StyledSubTitle
        :styles="{
          color: 'white',
          zIndex: 3,
        }"
        :text="rocket.country" />
    </GridContainer>
  </div>
</template>

<script>
import GridContainer from '@/components/Functional/GridContainer';
import StyledTitle from '@/components/Functional/StyledTitle';
import StyledSubTitle from '@/components/Functional/StyledSubTitle';

export default {
  name: 'RocketCard',
  props: {
    rocket: { type: Object, required: true },
    fluid: { type: Boolean, default: false },
  },
  components: { StyledTitle, GridContainer, StyledSubTitle },
};
</script>

<style lang="scss" scoped>
.card {
  position: relative;
  box-shadow: 0px 0px 30px #ccc;
  margin-bottom: 60px;
  background-size: cover;
  cursor: pointer;
  border-radius: 18px;

  &-overlay {
    border-radius: 18px;
    position: absolute;
    background-image: linear-gradient(135deg, #FF57B9 0%,#A704FD 100%);
    opacity: 0.4;
  }
}
</style>
