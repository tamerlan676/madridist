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
                a.not-model(href="https://wa.me/79288597799" target="_blank") Моей модели нет в списке
          .option
        button.add-to-cart(@click="addToCart(product)" :class="{ active: model !== '' }") Добавить в корзину

</template>

<script>
export default {
    data() {
        return {
            id: this.$route.params.id,
            model: '',
        }
    },
    async fetch ({ store }) {
        await store.dispatch('getMobileCases')
  },
  head(){
        return {
          title: this.getItem.title.rendered,
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
        margin-bottom: 24px;
        img{
            max-width: 100%;
        }
    }
    .product-wrapper{
        .image{
            display: none;
        }
        .info{
            h1{
                font-size: 24px;
                margin-bottom: 16px;
            }
            .desc{
                margin-bottom: 24px;
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
                    @media(min-width: 768px){
                    width: 300px;
                    }
                }
            }
            .not-model{
                color: rgb(67, 158, 81)
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
    }
}

</styles>