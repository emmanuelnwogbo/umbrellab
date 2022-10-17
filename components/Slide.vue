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

.slide {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    height: 103rem;
    transform: rotate(90deg) translateX(103rem) translateY(2rem);
    transform-origin: right top;
    transition: all 1s ease;

    animation: fadeinto 1s ease-in-out alternate;

    &::before {
        content: '';
        position: absolute;
        top: 12rem;
        left: 0;
        background: rgba(0, 0, 0, .35);
        height: 74.5rem;
        width: 100%;
        z-index: 4;
    }

    &__nav {
        position: absolute;
        top: 0;
        left: -3rem;
        z-index: 2;
        width: 3rem;
        height: 90rem;

        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;

        & span {
            display: inline-block;
            border-radius: 100%;
            background: rgba(255, 255, 255, .5);
            height: 1rem;
            width: 1rem;
            cursor: pointer;
            transition: all 1s ease;
            margin: .5rem 0;

            &.current {
                background: #fff;
            }
        }
    }

    &__label {
        position: absolute;
        top: 0;
        left: 0;
        height: 87rem;
        z-index: 5;
        padding-top: 47rem;
        padding-left: 1rem;
        color: #fff;


      animation: dropin 1.2s ease-in-out alternate;

        &--name {
            text-transform: uppercase;
            display: inline;
            font-weight: 600;
            font-size: 4rem;
            background: rgba(226, 155, 49, 1);
            padding: 1rem;
        }

        &--tag {
            margin-top: 2rem;
            font-size: 1.5rem;
            font-style: italic;
            width: 24rem;
            line-height: 2.5rem;
        }
    }

    &.quidax {
         width: 100rem;
    }

    &.chips {
        width: 100rem;
        transform: rotate(90deg) translateX(108rem) translateY(2rem);

        &::before {
            top: 12.2rem;
            height: 74rem;
        }
    }

    &.nestle {
        width: 62rem;
        transform: rotate(90deg) translateX(75rem) translateY(-35rem);

        &::before {
            top: 8.2rem;
            height: 82rem;
        }
    }

    &.cocacola {
        transform: rotate(90deg) translateX(77rem) translateY(-2rem);

        &::before {
            top: 13.3rem;
            height: 71.7rem;
        }
    }

    &.visa {
        width: 62rem;
        transform: rotate(90deg) translateX(44rem) translateY(-35rem);

        &::before {
            top: 8.3rem;
            height: 82rem;
        }
    }

    &.rebellion {
        position: absolute;
        width: 62rem;
        transform: rotate(90deg) translateX(11rem) translateY(-35rem);

        &::before {
            top: 8.3rem;
            height: 82rem;
        }
    }

    & img {
        position: absolute;
        top: 0;
        left: 0;
        height: 80%;
        width: 100%;
        object-fit: contain;
        transform: translateY(8rem);
        transition: all 1s ease;
        opacity: 0;

        &.visible {
            opacity: 1;
        }
    }
}
</style>
