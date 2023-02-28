<template lang="pug">
.banner
    .banner-wrapper
        .left
            h3 Есть вопросы?
            p Свяжитесь с нами и мы поможем вам, как Лука Модрич и Тони Кросс помогают своими партнерам по команде
            button связаться 
        .right
            img(src="~/assets/images/lukakross.jpg")
</template>

<script>
export default {
    name: 'BannerComp'
}
</script>

<style lang="scss" scoped>
.banner{
    padding: 16px;
    margin-bottom: 60px;
    .banner-wrapper{
        background: var(--blue);
        @media(min-width: 992px){
            display: flex;
            width: 900px;
            margin: 0 auto;
            justify-content: space-between;
        }
        @media(min-width: 1200px){
            width: 1200px;
        }
        .left{
            color: #fff;
            padding: 20px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            @media(min-width: 992px){
                width: 500px;
                padding: 32px;
            }
            @media(min-width: 1200px){
                width: 600px;
                padding: 32px;
            }
            h3{
                color: #fff;
                margin-bottom: 24px;
                @media(min-width: 992px){
                    font-size: 32px;
                }
            }
            p{
                margin-bottom: 24px;
            }
            button{
                background: #fff;
                color: var(--blue);
                padding: 15px 20px;
                text-transform: uppercase;
                width: 100%;
                font-weight: 500;
                @media(min-width: 992px){
                    width: 200px;
                }
            }
        }
        .right{
            display: none;
            @media(min-width: 992px){
                display: block;
            }
            img{
                max-width: 100%;
            }
        }
    }
}
</style>