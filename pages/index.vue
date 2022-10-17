<template>
  <div class="main">
    <!--<figure class="main__logo">
      <img src="@/assets/imgs/logo.svg"/>
    </figure>-->
    <div class="main__container">
      <div class="main__left">
        <h1>Where ideas </br> come to live</h1>
        <h3>Ideas light up the world, </br>execution keeps it spinning</h3>
      </div>
      <div class="main__right">
        <div class="main__slide">
          <div class="main__card" :class="{ 
            outoffocus: current !== 1,
            inview: current === 1,
            review: current === 2 || current === 3,
            invisiblereview: current === 3
            }" @click="$router.push('works')">
            <figure>
              <img src="@/assets/imgs/works.png" />
            </figure>
            <label class="yellow">Works</label>
          </div>
          <div class="main__card" :class="{ 
            outoffocus: current !== 2,
            inview: current === 2,
            review: current === 3
            }">
            <figure>
              <img src="@/assets/imgs/contact.png" />
            </figure>
            <label class="blue">Contact Us</label>
          </div>
          <div class="main__card" :class="{ 
            outoffocus: current !== 3,
            inview: current === 3,
            preview: current === 2
            }">
            <figure>
              <img src="@/assets/imgs/about.png" />
            </figure>
            <label class="orange">About Us</label>
          </div>
        </div>
        <div class="main__slidetoggle">
          <figure class="main__slidetoggle--btn" @click="decrease">
            <img src="@/assets/imgs/leftarrow.png" />
          </figure>
          <figure class="main__slidetoggle--btn" @click="increase">
            <img src="@/assets/imgs/rightarrow.png" />
          </figure>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      current: 1
    }
  },
  methods: {
    increase() {
      if (this.current <= 2) {
        console.log('increase')
        let current = this.current;
        current+=1;
        this.current = current;
      }
    },
    decrease() {
      if (this.current >=2 ) {
        let current = this.current;
        current-=1;
        this.current = current;
      }
    }
  }
}
</script>

<style lang="scss" scoped>
@function scaleValue($value) {
    @return calc(
      #{$value} * (clamp(350px, 100vw, 3840px) / var(--ideal-viewport-width));
    );
}

.main {
  position: relative;

  @include mainsidepadding;

  &__logo {
    @include logo
  }

  &__container {
    position: relative;
    display: flex;

    margin-top: 25rem;
    z-index: 2;
  }

  &__left {
    position: relative;
    color: #fff;
    z-index: 4;

    & h1 {
      font-size: 11rem;
      line-height: 12rem;
      font-weight: 800;
      animation: dropin 1.2s ease-in-out alternate;
      margin-bottom: 2rem;
    }

    & h3 {
      font-size: 3.5rem;
      font-weight: 500;
      animation: dropin 1.4s ease-in-out alternate;
    }
  }

  &__right {
    position: relative;
    margin-left: #{scaleValue(100)};
    animation: dropin 1.4s ease-in-out alternate;
  }

  &__card {
    position: absolute;
    top: 0;
    cursor: pointer;

    transition: all .5s ease-in;
    display: flex;
    justify-content: center;
    align-items: center;

    flex-direction: column;
    height: #{scaleValue(500)};
    width: #{scaleValue(500)};

    & label {
      text-transform: uppercase;
      font-size: 3rem;
      font-weight: 600;
      background: red;
      padding: 1.6rem 5rem;

      transition: all 1s ease;

      &.yellow {
        background: rgba(226, 155, 49, 1);
        transform: translateY(-14rem);
      }

      &.blue {
        background: rgba(49, 194, 226, 1);
        transform: translateY(-11rem);
      }

      &.orange {
        background: rgba(226, 81, 49, 1);
        transform: translateY(-4rem);
      }
    }

    &:nth-child(2) {
      transform: translateX(#{scaleValue(400)});
    }

    &:nth-child(3) {
      transform: translateX(#{scaleValue(400)});
      z-index: -1;
      opacity: 0;
    }

    &.review {
      transform: translateX(#{scaleValue(-450)});
    }

    &.inview {
      transform: translateX(#{scaleValue(-60)});
      opacity: 1;
    }

    &.preview {
      opacity: 1;
    }

    &.outoffocus {
      filter: blur(.3rem);

      & figure {
        transform: scale(.5);
      }

      & label {
        transform: scale(.7) translateY(-25rem);
      }
    }

    &.invisiblereview {
      transform: translateX(#{scaleValue(-750)});

      & figure {
        transform: scale(.35);
      }

      & label {
        transform: scale(.7) translateY(-30rem);
      }
    }

    & figure {
      height: 100%;
      width: 100%;

      transition: all 1s ease;

      & img {
        height: 100%;
        width: 100%;
        object-fit: contain;
      }
    }
  }

  &__slide {
    height: #{scaleValue(470)};
    width: 60rem;
    display: flex;
  }

  &__slidetoggle {
    display: flex;
    justify-content: center;
    position: relative;
    z-index: 5;

    &--btn {
      border-radius: 100%;
      height: 5rem;
      width: 5rem;
      background: rgba(70, 70, 70, 1);
      display: flex;
      justify-content: center;
      align-items: center;

      margin: 0 1rem;
      cursor: pointer;

      & img {
        height: 40%;
        width: 40%;
        object-fit: contain;
      }
    }
  }
}
</style>