<template>
  <figure class="logo" @click="$router.push('/')">
      <img src="@/assets/imgs/Group.svg"/>
  </figure>
</template>

<script>
  export default {
    
  }
</script>

<style lang="scss" scoped>
@function scaleValue($value) {
    @return calc(
      #{$value} * (clamp(350px, 100vw, 3840px) / var(--ideal-viewport-width));
    );
}

.logo {
  height: #{scaleValue(100)};
  width: #{scaleValue(120)};

  & img {
    height: 53%;
    width: 100%;
    object-fit: contain;
    cursor: pointer;
  }
}
</style>
