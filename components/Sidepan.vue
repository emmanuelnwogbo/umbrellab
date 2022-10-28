<template>
    <div class="sidepan">
         <Logo />
         <slot name="caption"></slot>
    </div>
</template>

<style lang="scss" scoped>
@function scaleValue($value) {
    @return calc(
      #{$value} * (clamp(350px, 100vw, 3840px) / var(--ideal-viewport-width));
    );
}

.sidepan {
    position: fixed;
    top: 0;
    left: 0;
    height: 100vh; 
    width: #{scaleValue(340)}; 
    background: #000000;
    z-index: 10;

    padding: #{scaleValue(40)}; 
    padding-left: #{scaleValue(100)}; 

    @media only screen and (max-width: 414px) {
        position: relative;
        height: #{scaleValue(1200)}; 
        width: 100vw;
    }

    &__figure {
        margin-top: #{scaleValue(140)}; 
        height: #{scaleValue(300)};
        width: #{scaleValue(300)};

        transform: translateX(#{scaleValue(-80)});

        @media only screen and (max-width: 414px) {
            height: #{scaleValue(700)};
            width: #{scaleValue(700)};
            margin-top: #{scaleValue(20)}; 
        }

        & img {
            object-fit: contain;
            height: 100%;
            width: 100%;
        }
    }

    &__label {
        display: inline-block;
        padding: #{scaleValue(15)} #{scaleValue(70)};
        font-size: #{scaleValue(30)};
        font-weight: 600;
        text-transform: uppercase;

        @media only screen and (max-width: 414px) {
            font-size: #{scaleValue(80)};
        }

        &.yellow {
            background: rgba(226, 155, 49, 1);
            transform: translateX(#{scaleValue(-60)}) translateY(#{scaleValue(-110)});

            @media only screen and (max-width: 414px) {
                transform: translateX(#{scaleValue(100)}) translateY(#{scaleValue(-110)});
            }
        }

        &.blue {
            background: rgba(49, 194, 226, 1);
            transform: translateX(#{scaleValue(-60)}) translateY(#{scaleValue(-110)});
        }

        &.orange {
            background: rgba(226, 81, 49, 1);
            transform: translateX(#{scaleValue(-60)}) translateY(#{scaleValue(-90)});
         }
    }
}
</style>