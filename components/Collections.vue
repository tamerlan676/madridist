<template lang="pug">
.collections
    h3.block-title Коллекции
    .collections-wrapper
        nuxt-link.collection(to="/collections/retro")
            h4.collection-name Retro
        nuxt-link.collection(to="/collections/retro")
            h4.collection-name Jerseys
        nuxt-link.collection(to="/collections/retro")
            h4.collection-name Minimalism
        nuxt-link.collection(to="/collections/retro")
            h4.collection-name Present
</template>
    
    <script>
      export default{
        name: 'CollectionsComponent',
        data() {
          return {
            retro: require('~/assets/images/retro.jpg'),
            forms: require('~/assets/images/forms.jpg'),
            minimalism: require('~/assets/images/minimalism.jpg'),
            present: require('~/assets/images/present.jpg'),
          }
        }
      }
    </script>
    
    <style lang="scss" scoped>
    .collections{
      padding: 40px 16px;
      @media(min-width: 1200px){
        padding: 120px 0;
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
          width: 1200px;
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
            background-size: cover;
            text-decoration: none;
            &:nth-child(1){
              background-image: url(../assets/images/retro-sm.jpg);
            }
            &:nth-child(2){
              background-image: url(../assets/images/forms-sm.jpg);
            }
            &:nth-child(3){
              background-image: url(../assets/images/minimalism-sm.jpg);
            }
            &:nth-child(4){
              background-image: url(../assets/images/present-sm.jpg);
            }
            @media(min-width: 768px){
              &:nth-child(1){
                background-image: url(../assets/images/retro.jpg);
              }
              &:nth-child(2){
              background-image: url(../assets/images/forms.jpg);
              }
              &:nth-child(3){
              background-image: url(../assets/images/minimalism.jpg);
              }
              &:nth-child(4){
              background-image: url(../assets/images/present.jpg);
              }
            }
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