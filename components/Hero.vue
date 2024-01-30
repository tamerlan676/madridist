<template lang="pug">
.hero
    .text 
        h1 Лучший подарок фанату Реал Мадрид
        p Уникальные чехлы для реальных&nbsp;фанатов
</template>

<script>
export default{
    name: 'heroComp'
}
</script>

<style lang="scss" scoped>
.hero{
    width: 100%;
    height: 450px;
    background-image: url(../assets/images/hero.jpg);
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