<template>
    <div class="works">
        <div class="works__sidepan">

        </div>
        <div class="works__slider" id="slider">
            <div v-for="item in images" class="works__slide">
                <Slide :images="item.images" :name="item.name" :itemclass="item.itemclass" :tag="item.tag"/>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                images: [
                    {
                        name: 'Quidax',
                        tag: 'Commercial Photography and creative direction',
                        itemclass: 'quidax',
                        images: [
                            'https://advertising-samson.s3.eu-west-2.amazonaws.com/quidax/Mask+group-1.png',
                            'https://advertising-samson.s3.eu-west-2.amazonaws.com/quidax/Mask+group-2.png',
                            'https://advertising-samson.s3.eu-west-2.amazonaws.com/quidax/Mask+group.png'
                        ]
                    },
                    {
                        name: 'Chief Chips',
                        tag: 'Branding, product design and advertising',
                        itemclass: "chips",
                        images: [
                            'https://advertising-samson.s3.eu-west-2.amazonaws.com/chiefchip/Mask+group.png',
                            'https://advertising-samson.s3.eu-west-2.amazonaws.com/chiefchip/Mask+group-2.png',
                            'https://advertising-samson.s3.eu-west-2.amazonaws.com/chiefchip/Mask+group-1.png',
                        ]
                    },
                    {
                        name: 'Nestle',
                        itemclass: 'nestle',
                        tag: 'Photography',
                        images: [
                            'https://advertising-samson.s3.eu-west-2.amazonaws.com/nestle/Mask+group-1.png',
                            'https://advertising-samson.s3.eu-west-2.amazonaws.com/nestle/Mask+group-2.png',
                            'https://advertising-samson.s3.eu-west-2.amazonaws.com/nestle/Mask+group.png'
                        ]
                    },
                    {
                        name: 'Cocacola',
                        itemclass: 'cocacola',
                        tag: 'Advertising',
                        images: [
                            'https://advertising-samson.s3.eu-west-2.amazonaws.com/coke/coke.png'
                        ]
                    },
                    {
                        name: 'Visa',
                        itemclass: 'visa',
                        tag: 'Advertising, Photography',
                        images: [
                            'https://advertising-samson.s3.eu-west-2.amazonaws.com/visa/Mask+group-1.png',
                            'https://advertising-samson.s3.eu-west-2.amazonaws.com/visa/Mask+group-2.png',
                            'https://advertising-samson.s3.eu-west-2.amazonaws.com/visa/Mask+group.png'
                        ]
                    },
                    {
                        name: 'Rebellion',
                        itemclass: 'rebellion',
                        tag: 'NFT, ART DIRECTION & PRODUCT DESIGN',
                        images: [
                            'https://advertising-samson.s3.eu-west-2.amazonaws.com/therebellion/Mask+group-1.png',
                        ]
                    },
                ]
            }
        },
        mounted() {}
    }
</script>

<style lang="scss" scoped>
@function scaleValue($value) {
    @return calc(
      #{$value} * (clamp(350px, 100vw, 3840px) / var(--ideal-viewport-width));
    );
}

.works {
    position: relative;
    z-index: 2;
    height: 100vh;
    transition: all .5s ease-in;
    display: flex;
    animation: fadeinto 1.5s ease-in-out alternate;
    
    &::before {
        content: '';
        position: fixed;
        bottom: 0;
        left: 0;
        height: 100vh;
        width: 100vw;
        background: rgba(20, 20, 20, 1);
        animation: grow .7s ease-in-out alternate;
    }
    
    &__sidepan {
        position: fixed;
        top: 0;
        left: 0;
        height: 100vh;
        width: 45rem;
        background: #000000;
    }

    &__slider {
        position: absolute;
        display: block;
        top: 0;
        left: 0;
        height: #{scaleValue(1280)}; 
        overflow-y: auto;
        overflow-x: hidden;
        padding-bottom: 30rem;
        transform: rotate(-90deg) translateY(-52rem);
        transform-origin: right top;
        width: 97rem;
    }
}
</style>