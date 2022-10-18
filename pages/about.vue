<template>
  <div class="about">
    <Sidepan>
        <template v-slot:caption>
            <figure class="sidepan__figure">
                <img src="@/assets/imgs/about.png" />
            </figure>
            <label class="sidepan__label orange">About</label>
        </template>
    </Sidepan>
    <div class="about__body">
        <div class="about__content">
            <h2 class="about__content--h2">Who are we?</h2>

            <p class="about__content--p">We are team of young visionaries with a mission to take creative ideation and execution for brands to the next level.We like to see ourselves as creative henchmen, we do the heavylifting and go to any length to bring your ideas to life. </p>
        </div>

        <div class="about__content">
            <h2 class="about__content--h2">Our process?</h2>

            <p class="about__content--p">Our process is simple. Think, expand and execute. We are not guided by logical and obvious conclusions. Our madness drives us to seek solutions where no one dares look at. </p>
        </div>
    </div>
  </div>
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

.about {
     @include pagelayout;

     &__body {
        position: relative;
        padding-left: #{scaleValue(367)}; 
        padding-top: #{scaleValue(180)}; 
     }

     &__content {
        width: #{scaleValue(1000)}; 
        
        &:nth-child(1) {
            margin-bottom: #{scaleValue(50)}; 
        }

        &--h2 {
            font-style: italic;
            font-size: #{scaleValue(45)}; 
            font-weight: 600;
            margin-bottom: #{scaleValue(10)}; 
            text-transform: uppercase;
        }

        &--p {
            font-size: #{scaleValue(30)}; 
            line-height: #{scaleValue(50)}; 
        }
     }
}
</style>
