<template lang="pug">
.collections
    h3.block-title Коллекции
    .collections-wrapper
        nuxt-link.collection(to=`#` v-for="item in 4")
            h4.collection-name Классика
</template>
    
    <script>
      export default{
        name: 'CollectionsComponent',
        data() {
          return {
          }
        }
      }
    </script>
    
    <style lang="scss" scoped>
    .collections{
      padding: 40px 16px;
      @media(min-width: 1200px){
        padding: 120px 0 60px;
      }
      .block-title{
        margin-bottom: 32px;
        font-size: 24px;
        text-align: center;
        @media(min-width: 1200px){
          margin-bottom: 40px;
          font-size: 32px;
        }
      }
      .collections-wrapper{
        display: grid;
        grid-gap: 20px;
        @media(min-width: 768px){
          grid-template-columns: 1fr 1fr;
        }
        @media(min-width: 992px){
          margin: 0 auto; 
        }
        @media(min-width: 1200px){
          width: 100%;
          padding: 0 40px;
          margin: 0 auto; 
          grid-template-columns: 1fr 1fr 1fr 1fr;
          box-sizing: border-box;
          
        }
        .collection{
            width: 100%;
            overflow: hidden;
            height: 300px;
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 30px;
            box-sizing: border-box;
            text-align: center;
            transition: all .5s ease;
            background: url(../assets/images/collection.webp);
            background-size: cover;
            text-decoration: none;
            @media(min-width: 992px){
            height: 400px; 
            background-position:  center;
            }
            @media(min-width: 1200px){
            height: 500px; 
            }
            &:before{
            content: '';
            top: 0;
            width: 100%;
            height: 100%;
            position: absolute;
            background-color: var(--blue);
            opacity: 0.5;
            z-index: 1;
            transition: all .5s ease;
            }
            &:hover{
            &:before{
                opacity: 0.3;
            }
            }
        .collection-name{
          color: #fff;
          z-index: 2;
          font-size: 23px;
          text-decoration: none;
          @media(min-width: 992px){
            font-size: 24px; 
          }
        }
      }
      }
    }
    </style>