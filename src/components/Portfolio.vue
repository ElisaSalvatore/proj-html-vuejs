<template>
    <div>
        <div class="section-container">
            <div class="section-top">
                <span class="text">
                    <div class="section-name">Portfolio</div>
                    <span class="section-title"><b>latest</b> work</span>
                </span>

                <span class="arrows-slider">
                    <button>&#x2190;</button>
                    <button>&#x2192;</button>
                </span>
            </div>

            <div class="section-down">
                <div class="slider shadow-gray" v-for="(image, i) in images" :key="i">
                    <img :src="require(`../assets/images/${image.url}.jpg`)">
                    <div class="slider-text">
                        <div class="title">{{image.title}}</div>
                        <div class="category">{{image.category}}</div>
                    </div>
                </div>
            </div>

            <div class="slider-points">
                <div v-for="(image, currentIndex) in images" :key="currentIndex" :class="['point', currentIndex == indexImage ? 'active': 'disable']"></div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Portfolio',
    data() {
        return {
            images: [
               {
                url: 'a247b00b-3621-470f-b4b8-b3ac46f25907-1-790x576',
                title: 'Satisfy Poster',
                category: 'Branding Startegy',
               },
               {
                url: 'DRY-1-790x576',
                title: 'Purinky Products',
                category: 'Digital Experience',
               },
               {
                url: '8wa60okr-1-790x576',
                title: 'Basket of Flower on table',
                category: 'Branding Startegy',
               },
               {
                url: '84316050-0af0-49db-a53a-241d47ddad0e-2-790x576',
                title: 'Mock-up',
                category: 'Digital Experience',
               }, 
            ],
            currentIndex: 0,        
        }
    },
    // methods: {
    //     prevImage() {
    //         this.currentIndex--;
    //         if (this.currentIndex < 0) {
    //             this.currentIndex = this.image.length - 1;
    //         }
    //     },
    //     nextImage () {
    //         this.currentIndex++;
    //         if (this.currentIndex >= this.image.length) {
    //             this.currentindex = 0;
    //         }
    //     },
    // }
    
}
</script>

<style lang="scss" scoped>
@import '@/style/sectionsHeading.scss';

.section-container {
    text-align: start;
    background-color: #fff;
    margin-bottom: 20px;

    .section-top {
        display: flex;
        justify-content: space-between;
        align-items: flex-end;
        padding: 0 60px;

        .arrows-slider  {
            display: flex;
            justify-content: center;
            align-items: center;
            
            > button {
                height: 40px;
                margin: 10px;
                padding: 6px 8px;
                font-size: 20px;
                color: $light-pink;
                border: 1px solid $light-pink;
                border-radius: 50px;
                background-color: #fff;

                &:hover {
                    cursor: pointer;
                    background-color: $light-pink;
                    color: #fff;
                }
            }
            
        }
    }

    .section-down {
        margin: 0 auto;
        height: 325px;
        display: flex;
        justify-content: center;
        padding: 20px 0;

        .slider {
            justify-content: space-between;
            align-items: center;
            width: calc(100% / 4 - 60px);
            margin: 30px;
            background-color: #fff;
            border-radius: 20px;
            
            > img {
                width: 100%;
                min-height: 200px;
                border-radius: 20px;
            }

            .slider-text {
                display: flex;
                justify-content: space-between;
                align-items: center;
                padding: 20px 10px ;

                .title {
                    font-size: 11px;
                    font-weight: 600;
                }

                .category {
                    font-size: 10px;
                    color: $text-gray;
                }
            }

            // da DISATTIVARE in caso di slider dinamico
            &:first-of-type {
                color: #fff;
                background-color: $dark-pink;
                background-image: linear-gradient(
                    to left,
                    $light-pink,
                    $dark-pink, 
                );

                .category {
                    color: #fff;
                }
            }

            // HOVER SLIDER DINAMICO
            &:hover { 
                color: #fff;
                background-color: $dark-pink;
                background-image: linear-gradient(
                    to left,
                    $light-pink,
                    $dark-pink, 
                );

                .category {
                    color: #fff;
                }
            }
        }
    }

    .slider-points {
        margin: 0 auto;
        display: flex;
        justify-content: space-between;
        align-items: center;
        width: 100px;

        .point {
            width: 10px;
            height: 10px;
            border-radius: 50%;
            margin: 0 5px;
            background-color: $text-gray;

            // DA DISATTIVARE in caso di slider dinamico
            &:first-of-type {
                background-color: $light-pink;
            }
            
            // DA ATTIVARE in caso di slider dinamico
            // .active {
            //     background-color: $light-pink;
            // }

            // .disable {
            //     background-color: $text-gray;
            // }
        }

    }
}
</style>