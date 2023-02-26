<template lang="pug">
.banner
    .text 
        h1 MADRIDIST
        p Уникальные сувениры для реальных&nbsp;фанатов
</template>

<script>
export default{
    name: 'BannerComp'
}
</script>

<style lang="scss" scoped>
.banner{
    width: 100%;
    height: 450px;
    background-image: url(../assets/images/banner.jpg);
    background-size: cover;
    background-position: center;
    position: relative;
    @media(min-width: 992px){
        height: 600px;
    }
    .text{
        position: absolute;
        bottom: 0;
        width: 100%;
        padding: 40px;
        background: rgb(17,32,56);
        background: linear-gradient(0deg, rgba(17,32,56,0.7511598389355743) 80%, rgba(17,32,56,0.8996192226890756) 100%);
        color: #fff;
        text-align: center;
        box-sizing: border-box;
        h1{
            letter-spacing: 10px;
            margin-bottom: 10px;
            @media(min-width: 992px){
                font-size: 40px;
            }
        }
        p{
            line-height: 24px;
            @media(min-width: 992px){
                font-size: 18px;
            }
        }
    }
}
</style>