<template>
    <div class="works">
        <Sidepan>
            <template v-slot:caption>
                <figure class="sidepan__figure">
                    <img src="@/assets/imgs/works.png" />
                </figure>
                <label class="sidepan__label yellow">Works</label>
            </template>
        </Sidepan>
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
    @include pagelayout;

    &__slider {
        position: absolute;
        display: block;
        top: 0;
        left: 0;
        height: #{scaleValue(1900)}; 
        overflow-y: auto;
        overflow-x: hidden;
        transform: rotate(-90deg) translateY(#{scaleValue(-550)}) translateX(#{scaleValue(-20)});
        transform-origin: right top;
        width: #{scaleValue(900)}; 
    }
}
</style>