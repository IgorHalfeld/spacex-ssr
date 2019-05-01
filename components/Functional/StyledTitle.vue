<template functional>
  <h1
    :style="props.styles || {}"
    class="title">{{ props.title }}</h1>
</template>

<style lang="scss" scoped>
.title {
  font-family: Lobster;
  font-size: 3rem;
  color: #C18DE4;
}
</style>
