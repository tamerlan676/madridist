<template lang="pug">
.hits 
    h2 Хиты продаж
    .hits-wrapper
        nuxt-link.hit(to="#" v-for="item in 8") 
                .hit-img
                    img(src="~/assets/images/case.jpg") 
                .hit-info 
                    h3 Чехол простой
                    .old-price 1800 ₽
                    .price 1100 ₽
    
</template>

<script>
export default {
    name: 'HitsComponent',
    data () {
        return {

        }
    }
}
</script>

<style lang="scss" scoped>
.hits{
    padding: 40px 16px;
    h2{
        text-align: center;
        margin-bottom: 32px;
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