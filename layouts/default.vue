<template lang="pug">
.default
    Header(@turnMenu="turnMenu" :activeBurger="activeBurger" @turnCart="turnCart")
    .mob-menu(:class="{active: menuActive}")
        ul.parent-ul
            li.parent-li(@click="checkMenuElem(item)" v-for="item in menu") 
                nuxt-link.parent-a(:to="item.link") {{ item.title }}
                    .icon(v-if="item.subitems" :class="{ turned: item.sub }")
    CartPanel(:class="{active: cartActive}" @turnCart="turnCart")
    Nuxt
    Footer
    .floating-call-btn 
      a(href="https://wa.me/79188208097")
        .pulse
          img(src="~/assets/images/fl-wts.svg")
</template>

 <script>
 export default {
    data() {
        return {
            menu: [
              {
                title: 'Главная',
                link: '/',
              },
              {
                title: 'О Компании',
                link: '/about',
              },
              {
                title: 'Доставка и оплата',
                link: '/delivery',
              },
              {
                title: 'Контакты',
                link: '/contacts',
              }
            ],
            activeBurger: false,
            menuActive: false,
            cartActive: false
        }
    },
    methods: {
        turnMenu() {
            this.menuActive = !this.menuActive;
            this.activeBurger = !this.activeBurger;
            if (this.cartActive) {
                this.cartActive = false;
                this.fixBody()
            }
        },
        checkMenuElem(item){
          if(item.subitems){
            item.sub = !item.sub
          }else{
            location.href = item.link;
            this.turnMenu()
          }
        },
        turnCart() {
            this.cartActive = !this.cartActive;
            if (this.menuActive && this.activeBurger) {
                this.menuActive = false;
                this.activeBurger = false;
            }
            // this.fixBody()
        },
        // fixBody(){
        //   if(this.cartActive === true){
        //     const x=window.scrollX;
        //     const y=window.scrollY;
        //     window.onscroll=function(){window.scrollTo(x, y);};
        //   }
        //   if(this.cartActive === false){
        //     window.onscroll=function(){};
        //   }
        // }
    },
 }
 </script>

<style lang="scss" scoped>
.default{
  position: relative;
  .mob-menu{
    position: fixed;
    width: 100%;
    height: 100%;
    left: -100%;
    transition: all .5s ease;
    box-sizing: border-box;
    overflow-y: scroll;
    z-index: 20;
    top: 125px;
    background: #fff;
    box-shadow: 4px 4px 8px 0px rgba(34, 60, 80, 0.2);
    padding-bottom: 20px;
    @media(min-width: 992px){
      display: none;
    }
    &.active{
      left: 0;
    }
    .parent-ul{
      padding: 16px;
      .parent-li{
        font-size: 18px;
        padding: 10px;
        border-bottom: 1px solid rgb(205, 205, 205);
        position: relative;
        .parent-a{
          font-weight: 500;
          text-transform: uppercase;
          color: #000
        }
        .icon{
          position: absolute;
          top: 20px;
          width: 10px;
          height: 10px;
          background-size: contain;
          right: 10px;
          background-repeat: no-repeat;
          background-image: url(~/assets/images/next.svg);
          transition: all .3s linear;
          transform: rotate(90deg);
          &.turned{
            transform: rotate(-90deg);
          }
        }
      }
    }
  }
  .floating-call-btn{
          position: fixed;
          bottom: 10%;
          right: 20px;
          .pulse {
            width: 55px;
            height: 55px;
            border-radius: 50px;
            background: #fbb32f;
            animation: pulse 1500ms infinite;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        @keyframes pulse {
          0% {
            box-shadow: 0 0 0 0 #0f8411;
          }
          100% {
            box-shadow: 0 0 0 17px #fbb32f01;
          }
        }
        }
}
</style>