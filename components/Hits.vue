<template lang="pug">
.hits 
    h2 Чехлы - Конструкторы
    .collection-desc Добавь любое имя и номер на свой чехол
    .hits-wrapper
        nuxt-link.hit(v-for="(item, key) in constructors" :key="key" :to="item.link") 
            .hit-img
                img(:src="item.image") 
            .hit-info 
                h3 {{ item.title }}
                .old-price 2300 ₽
                .price 1500 ₽
    
</template>

<script>
export default {
    name: 'HitsComponent',
    data () {
        return {
            constructors: [
                {
                    title: 'Season 19-20',
                    image: require('~/assets/images/constructors/americano.jpg'),
                    link: '/constructors/19-20'
                },
                {
                    title: 'Season 22',
                    image: require('~/assets/images/constructors/22-season.jpg'),
                    link: '/constructors/22-season'
                },
                {
                    title: 'Season 22-23',
                    image: require('~/assets/images/constructors/22-23.jpg'),
                    link: '/constructors/22-23'
                },
                {
                    title: 'Season 24-25',
                    image: require('~/assets/images/constructors/24.jpg'),
                    link: '/constructors/24'
                },
            ]
        }
    }
}
</script>

<style lang="scss" scoped>
.hits{
    padding: 40px 16px;
    @media(min-width: 992px){
        padding: 120px 0;
    }
    h2{
        margin-bottom: 16px;
        text-align: center;
        font-size: 24px;
        @media(min-width: 992px){
            font-size: 32px;
        }
    }
    .collection-desc{
        margin-bottom: 40px;
        font-style: italic;
        text-align: center;

    }
    .hits-wrapper{
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 10px;
        @media(min-width: 992px){
            grid-template-columns: repeat(4, 1fr);
            grid-gap: 20px;
        }
        @media(min-width: 1200px){
            margin: 0 auto;
            width: 1200px;
        }
        .hit{
            border: 1px solid #f2f2f2;
            padding: 15px;
            text-decoration: none;
            img{
                max-width: 100%;
            }
            h3{
                font-weight: normal;
                color: var(--blue);
                font-size: 13px;
                min-height: 40px;
                @media(min-width: 768px){
                    font-size: 16px;
                }
            }
            .old-price{
                font-size: 14px;
                text-decoration: line-through;
                color: grey;
                @media(min-width: 768px){
                    font-size: 16px;
                }
            }
            .price{
                font-weight: bold;
                color: var(--blue);
                @media(min-width: 768px){
                    font-size: 18px;
                }
            }
        }
    }

}

</style>