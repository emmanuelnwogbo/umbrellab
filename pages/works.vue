<template>
    <div class="works">
        <div class="works__sliderprogress" id="sliderindicator"></div>
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
        mounted() {
            console.log('mounted');
            const slider = document.getElementById('slider');
            slider.onscroll = () => {
                animateProgressIndicator()
            };

            function animateProgressIndicator() {
                let winScroll = slider.scrollTop || slider.scrollTop;
                let height = slider.scrollHeight - slider.clientHeight;
                let scrolled = (winScroll / height * 100);
                document.getElementById("sliderindicator").style.width = scrolled + "%";
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
        transform: rotate(-90deg) translateY(#{scaleValue(-510)}) translateX(#{scaleValue(-50)});
        transform-origin: right top;
        width: #{scaleValue(850)}; 
    }

    &__sliderprogress {
        position: absolute;
        top: 0;
        left: #{scaleValue(340)};
        height: #{scaleValue(3)}; 
        width: 0;
        background: #fff; 
        z-index: 12;
        transition: all .1s ease;
    }
}
</style>