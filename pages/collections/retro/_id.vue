<template lang="pug">
.inner-product 
    .mobile-image
        img(:src="getItem.acf.image")
    .product-wrapper 
        .image 
            img(:src="getItem.acf.image")
        .info 
          h1 {{ getItem.title.rendered }}
          .desc(v-html="getItem.acf.description") {{ getItem.acf.description }}
          .options 
            .option
                h4 Для заказа выберите модель телефона
                select(v-model="model")
                    option(disabled value="") Выберите один из вариантов
                    option(v-for="(item, key) in getModels" :key="key") {{ item }}
                a.not-model(href="https://wa.me/79188208097" target="_blank") Моей модели нет в списке
          .option
          button.add-to-cart(@click="addToCart(product)" :class="{ active: model !== '' }") Добавить в корзину
          .icons-info 
              .info-item(v-for="item in iconsInfo") 
                img(:src="item.img")
                .text(v-html="item.text") {{ item.text }}
    Banner

</template>

<script>
export default {
    data() {
        return {
            id: this.$route.params.id,
            model: '',
            iconsInfo: [
              {
                img: require("~/assets/images/quality.svg"),
                text: `<span>Изготовление</span>: Срок изготовления чехла чаще всего занимает 2 дня.`
              },
              {
                img: require("~/assets/images/quality.svg"),
                text: `<span>Доставка</span>: Доставим почтой России или любой другой ТК за 2-4 дня.`
              },
              {
                img: require("~/assets/images/quality.svg"),
                text: `<span>Материалы</span>: Чехол изготовлен из высококачественного пластика`
              },
              {
                img: require("~/assets/images/quality.svg"),
                text: `<span>Печать</span>: Используется рельефная и объемная печать с высокой цветопередачей`
              },
          ],
        }
    },
    async fetch ({ store }) {
        await store.dispatch('getMobileCases')
  },
  head(){
        return {
          title: 'Чехол фаната Реал Мадрид',
          meta: [
            { hid: 'description', name: 'description', content: 'Заказать чехол Реал Мадрид можно на нашем сайте madridits.ru' },
          ]
    }
  },
  computed: {
    getItem() {
      return this.$store.state.mobileCases.filter(item => item.id === +this.$route.params.id)[0]
    },
    getModels() {
      return this.$store.state.models
    },
    product() {
      return {
        title: this.getItem.title.rendered,
        id: this.id,
        model: this.model,
        price: +this.getItem.acf.price,
        image: this.getItem.acf.image
      }
    }
  },
  methods: {
    addToCart(product) {
      this.$store.commit('addToCart', product)
      this.addedMessage = true
      setTimeout(() => {
        this.addedMessage = false
      }, 1500)
    },
  }
}
</script>

<styles scoped lang="scss">
.inner-product{
    padding: 16px;
    .mobile-image{
        width: 100%;
        margin: 0 auto 24px;
        @media(min-width: 768px){
          width: 300px;
        }
        @media(min-width: 992px){
          display: none;
        }
        img{
            max-width: 100%;
        }
    }
    .product-wrapper{
      display: flex;
      justify-content: space-between;
      align-items: center;
      @media(min-width: 992px){
        margin-bottom: 60px;
      }
      @media(min-width: 1200px){
        width: 1200px;
        margin: 0 auto 60px;
      }
        .image{
            display: none;
            @media(min-width: 992px){
              display: block;
              width: 400px;
            }
            img{
              max-width: 100%;
            }
          }
        .info{
          width: 100%;
          @media(min-width: 992px){
              width: 500px;
            }
            @media(min-width: 1200px){
              width: 700px;
            }
            h1{
                font-size: 24px;
                margin-bottom: 16px;
            }
            .desc{
                margin-bottom: 24px;
                @media(min-width: 1200px){
                  width: 500px;
                }
            }
            .option{
                margin-bottom: 16px;
                h4{
                    margin-bottom: 8px;
                }
                select{
                    width: 100%;
                    font-size: 16px;
                    padding: 5px;
                    height: 40px;
                    margin-bottom: 4px;
                    border: 2px solid #000;
                    color: #000;
                    background: transparent;
                    cursor: pointer;
                    @media(min-width: 768px){
                    width: 300px;
                    }
                }
            }
            .not-model{
                color: rgb(67, 158, 81);
                display: block;
            }
        }
        .add-to-cart{
            width: 100%;
            background: #e5e5e5;
            padding: 15px;
            color: #fff;
            text-transform: uppercase;
            font-weight: 800;
            transition: .5s ease;
            margin-bottom: 24px;
            pointer-events: none;
            border-radius: 8px;
            @media(min-width: 768px){
                width: 300px;
            }
            &.active{
            background: #005bff;
            pointer-events: all;
            }
        }
        .icons-info{
              .info-item{
                display: flex;
                align-items: center;
                justify-content: center;
                margin-bottom: 24px;
                font-size: 14px;
                @media(min-width: 992px){
                  width: 400px;
                }
                img{
                  margin-right: 20px;
                  width: 30px;
                }
              }
            }
    }
}

</styles>