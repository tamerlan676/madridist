<template lang="pug">
section.reviews
    h2.section-title Отзывы
    p.section-desc Ознакомьтесь с мнением наших довольных клиентов
    .reviews-wrapper
        .review(v-for="(review, i) in reviews" :key="i")
            .header 
                .source {{ review.source }} 
                .name {{ review.name }}
            .main
                img.circle(:src="review.img" @click="index = i")
                .text {{ review.text }}
</template>
    
    <script>
    export default {
        name: 'ReviewsComp',
      data() {
        return {
          reviews: [
            {
                img: require("~/assets/images/reviews/1.jpg"),
                bigImg: require("~/assets/images/case.jpg"),
                source: 'WhatsApp',
                name: 'Наталья',
                text: 'Добрый день.Забрали чехол.Чехол хорошего качества ,яркий ,красивый -сын доволен 👍'
            },
            {
                img: require("~/assets/images/reviews/2.jpg"),
                bigImg: require("~/assets/images/reviews/2.jpg"),
                source: 'WhatsApp',
                name: 'Месроп',
                text: 'В целом все нравится! Нравится что имя рельефное и шрифт фирменный) Посмотрим как со временем себя будет вести'
            },
            {
                img: require("~/assets/images/reviews/3.jpg"),
                bigImg: require("~/assets/images/reviews/3.jpg"),
                source: 'WhatsApp',
                name: 'Артем',
                text: 'Добрый день! Все хорошо, очень нравится чехол. Удобный и пока нет потертостей)'
            },
            {
                img: require("~/assets/images/reviews/4.jpg"),
                bigImg: require("~/assets/images/reviews/4.jpg"),
                source: 'Instagram',
                name: 'Мурат',
                text: 'У меня в коллекции уже 3 чехла) Сейчас заказал с Ди Стефано. Первые два приходили без упаовки, а третий уже в фирменном пакете. Изображение четкое. Все нравится в целом'
            },
            {
                img: require("~/assets/images/reviews/5.jpg"),
                bigImg: require("~/assets/images/reviews/5.jpg"),
                source: 'WhatsApp',
                name: 'Виталий',
                text: 'Даже лучше чем я представлял! И шли не так долго) Думаю скоро закажу еще'
            },
            {
                img: require("~/assets/images/reviews/6.jpg"),
                bigImg: require("~/assets/images/reviews/6.jpg"),
                source: 'WhatsApp',
                name: 'Андрей',
                text: 'Добрый день!!! Получил чехлы , сели идеально 👍👍👍качество отличное👌👌👌всем доволен, благодарю👏👏👏'
            },
          ],
          images: [
            require("~/assets/images/reviews/1.jpg"),
            require("~/assets/images/reviews/2.jpg"),
            require("~/assets/images/reviews/3.jpg"),
            require("~/assets/images/reviews/4.jpg"),
            require("~/assets/images/reviews/5.jpg"),
            require("~/assets/images/reviews/6.jpg"),
          ],
          index: null,
        }
      }
    }
    </script>
    
    <style lang="scss" scoped>
    .reviews{
        h2{
            text-align: center;
            margin-bottom: 20px;
        } 
        p{
            text-align: center;
        }
        a{
            display: block;
            margin: 0 auto; 
        }
        padding: 80px 16px;
        background: #F6F6F6;
        @media(min-width: 992px){
            padding: 120px 32px;
        }
        p{
            margin-bottom: 40px;
        }
        .reviews-wrapper{
            @media(min-width: 992px){
                display: grid;
                grid-template-columns: 1fr 1fr;
                grid-gap: 20px;
                margin-bottom: 40px;
            }
            @media(min-width: 1200px){
                width: 1120px;
                margin: 0 auto 40px;
            }
            .review{
                background: #fff;
                padding: 16px;
                margin-bottom: 20px;
                @media(min-width: 992px){
                    margin-bottom: 0;
                }
                .header{
                    display: flex;
                    justify-content: flex-end;
                    margin-bottom: 16px;
                    .source{
                        margin-right: 50px;
                        font-weight: bold;
                    }
                    .name{
                        font-weight: bold;
                    }
                }
                .main{
                    display: flex;
                    justify-content: space-between;
                    .circle{
                        width: 50px;
                        height: 50px;
                        border: 4px solid #e5e5e5;
                        border-radius: 100%;
                        margin-right: 20px;
                        cursor: pointer
                    }
                    .text{
                        width: fit-content;
                    }
                }
            }
        }
        .transp-btn{
            border: 1px solid #000;
            color: #000;
            @media(min-width: 992px){
                width: 300px;
                margin: 0 auto;
            }
        }
    }
    </style>
    