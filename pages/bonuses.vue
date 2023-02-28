<template lang="pug">
.static-page 
    h1 Акции и бонусы
    p(v-html="text") {{  text  }}
</template>

<script>
export default {
    data() {
        return {
            text: 'акции и бонусы'
        }
    }
    
}
</script>

<style lang="scss" scoped>
.static-page{
    padding: 16px;
    margin-bottom: 40px;
    @media(min-width: 1200px){
        width: 900px;
        margin: 0 auto 120px;
        padding: 32px 0;
    }
    h1{
        margin-bottom: 24px;
    }

}

</style>