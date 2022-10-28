<template>
  <div class="slide__body">
    <figure :class="`slide ${itemclass}`">
        <div class="slide__nav">
            <span v-for="toggle in images" :class="{ current: current === toggle }" @click="togglevisible(toggle)"></span>
        </div>
        <div class="slide__label">
            <div class="slide__label--name">
                <span>{{ name }}</span>
            </div>
            <div class="slide__label--tag">
                <span>{{ tag }}</span>
            </div>
        </div>
        <img v-for="image in images" :src="image" :class="{ visible: current === image }"/>
    </figure>
  </div>
</template>

<script>
  export default {
    props: ['images', 'name', 'itemclass', 'tag'],
    data() {
        return {
            current: this.images[0],
            flipper: 0
        }
    },
    methods: {
        flip() {
            setInterval(() => {
                if (this.flipper === this.images.length -1) {
                    let flipper = this.flipper;
                    this.flipper = 0;
                    this.current = this.images[this.flipper];
                    return;
                }

                if (this.flipper < this.images.length-1) {
                    let flipper = this.flipper;
                    flipper += 1;
                    this.flipper = flipper;
                    this.current = this.images[this.flipper]
                }
            }, 3000)
        },
        togglevisible(val) {
            let flipper = this.images.indexOf(val);
            this.flipper = flipper;
            this.current = this.images[this.flipper]
        }
    },
    mounted() {
        this.flip();
    }
  }
</script>

<style lang="scss" scoped>
@function scaleValue($value) {
    @return calc(
      #{$value} * (clamp(350px, 100vw, 3840px) / var(--ideal-viewport-width));
    );
}

.slide {
    position: relative;
    height: #{scaleValue(920)}; 
    width: #{scaleValue(1010)};

    &::before {
        content: '';
        position: absolute;
        top: #{scaleValue(4)};
        left: 0;
        background: rgba(0, 0, 0, .35);
        height: #{scaleValue(730)};
        width: 100%;
        z-index: 4;
    }

    &.quidax {
         width: #{scaleValue(980)};
         transform: rotate(90deg) translateX(#{scaleValue(60)}) translateY(#{scaleValue(130)});
    }

    &.chips {
        width: #{scaleValue(980)};
        transform: rotate(90deg) translateX(#{scaleValue(190)}) translateY(#{scaleValue(130)});

        &::before {
            top: #{scaleValue(5)};
            height: #{scaleValue(726)};
        }
    }

    &.nestle {
        width: #{scaleValue(600)};
        height: #{scaleValue(1000)};
        transform: rotate(90deg) translateX(#{scaleValue(90)}) translateY(#{scaleValue(-55)});

        @media only screen and (max-width: 414px) {
            height: #{scaleValue(2200)};
        }

        &::before {
            top: #{scaleValue(4)};
            height: #{scaleValue(792)};
        }
    }

    &.cocacola {
        width: #{scaleValue(980)};
        transform: rotate(90deg) translateX(#{scaleValue(-13)}) translateY(#{scaleValue(130)});

        @media only screen and (max-width: 414px) {
            height: #{scaleValue(1200)};
        }

        &::before {
            top: #{scaleValue(5)};
            height: #{scaleValue(725)};
        }
    }

    &.visa {
        width: #{scaleValue(600)};
        height: #{scaleValue(1000)};
        transform: rotate(90deg) translateX(#{scaleValue(-115)}) translateY(#{scaleValue(-55)});

        @media only screen and (max-width: 414px) {
            height: #{scaleValue(2500)};
        }

        &::before {
            top: #{scaleValue(4)};
            height: #{scaleValue(792)};
        }
    }

    &.rebellion {
        width: #{scaleValue(600)};
        height: #{scaleValue(1000)};
        transform: rotate(90deg) translateX(#{scaleValue(-455)}) translateY(#{scaleValue(-55)});

        @media only screen and (max-width: 414px) {
            height: #{scaleValue(2600)};
        }

        &::before {
            top: #{scaleValue(4)};
            height: #{scaleValue(792)};
        }
    }

    & img {
        position: absolute;
        top: 0;
        left: 0;
        height: 80%;
        width: 100%;
        object-fit: contain;
        transition: all 1s ease;

        opacity: 0;

        @media only screen and (max-width: 414px) {
            height: 100%;
            width: 100%;
            object-fit: cover;
        }

        &.visible {
            opacity: 1;
        }
    }

    &__label {
        position: absolute;
        top: 0;
        left: 0;
        height: #{scaleValue(400)}; 
        z-index: 5;
        padding-top: #{scaleValue(400)}; 
        padding-left: #{scaleValue(10)}; 
        color: #fff;


        animation: dropin 1.2s ease-in-out alternate;

        @media only screen and (max-width: 414px) {
            padding-top: #{scaleValue(500)}; 
            padding-left: #{scaleValue(40)}; 
        }

        &--name {
            text-transform: uppercase;
            display: inline;
            font-weight: 600;
            font-size: #{scaleValue(35)}; 
            background: rgba(226, 155, 49, 1);
            padding: #{scaleValue(10)}; 

            @media only screen and (max-width: 414px) {
                font-size: #{scaleValue(100)}; 
                 margin-top: #{scaleValue(40)};
            }
        }

        &--tag {
            margin-top: #{scaleValue(20)}; 
            font-size: #{scaleValue(15)}; 
            font-style: italic;
            width: #{scaleValue(200)}; 
            line-height: #{scaleValue(25)}; 

            @media only screen and (max-width: 414px) {
                font-size: #{scaleValue(80)}; 
                line-height: #{scaleValue(100)}; 
                width: #{scaleValue(1000)}; 
                margin-top: #{scaleValue(40)};
            }
        }
    }

    &__nav {
        position: absolute;
        top: 0;
        left: #{scaleValue(-30)}; 
        z-index: 2;
        width: #{scaleValue(30)}; 
        height: #{scaleValue(800)};

        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;

        & span {
            display: inline-block;
            border-radius: 100%;
            background: rgba(255, 255, 255, .5);
            height: #{scaleValue(10)}; 
            width: #{scaleValue(10)}; 
            cursor: pointer;
            transition: all 1s ease;
            margin: #{scaleValue(5)} 0;

            &.current {
                background: #fff;
            }
        }
    }

    @media only screen and (max-width: 414px) {
        transform: none !important;
        width: 100vw !important;
        height: #{scaleValue(1200)}; 

        &::before {
            top: 0!important;
            height: 100% !important;
            background: rgba(0, 0, 0, .5);
        }
    }
}

</style>
