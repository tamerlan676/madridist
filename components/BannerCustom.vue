<template lang="pug">
.banner
    .banner-wrapper
        .left
            h3 Ничего не нравится?
            p Мы можем изготовить чехол по твоему персональному дизайну. Давай обсудим это
            a(href="https://wa.me/79188208097" target="_blank") Обсудить 
        .right
            img(src="~/assets/images/descust.jpg")
</template>

<script>
export default {
    name: 'BannerComp'
}
</script>

<style lang="scss" scoped>
.banner{
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
                line-height: 24px;
            }
            a{
                background: #fff;
                color: var(--blue);
                padding: 15px 20px;
                text-transform: uppercase;
                width: 100%;
                font-weight: 500;
                text-align: center;
                @media(min-width: 992px){
                    width: 200px;
                }
            }
        }
        .right{
            
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