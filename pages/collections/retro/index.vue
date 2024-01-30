<template lang="pug">
.collections-list
    h1 Retro
    .collection-desc Память как и легенды - бессмертна!
    .collection-wrapper 
        nuxt-link.product(v-for="(item, key) in collection" :key="key" :to="`/collections/retro/${item.id}`") 
            .product-img
                img(:src="item.acf.image") 
            .product-info 
                h3 {{ item.title.rendered }}
                .old-price {{ item.acf.old_price }} ₽
                .price {{ item.acf.price }} ₽

        seoTitle
    
</template>

<script>
    export default{
    name: "SlugCategory",
    async fetch({ store, params }) {
      const options = {
        collectionName: 'Retro'
      }
        await store.dispatch("getCollection", options);
    },
    head(){
        return {
          title: `Чехлы Real Madrid ${this.item.acf.seo_title} `,
          meta: [
              { hid: 'description', name: 'description', content: 'Выбирай уникальный дизайнерский чехол на свой телефон' },
          ]

        }
    },
    computed: {
        collection() {
            return this.$store.state.collection;
        },
        seoTitle() {
            return this.$store.state.collection.filter(item => item.id === +this.$route.params.id)[0]
        }
    }
}
  </script>


<style lang="scss" scoped>
.collections-list{
    padding: 16px;
    @media(min-width: 1200px){
            margin: 0 auto;
            width: 1200px;
            padding: 40px 0;
    }
    h1{
        margin-bottom: 16px;
    }
    .collection-desc{
        margin-bottom: 24px;
        font-style: italic;
    }
    .collection-wrapper{
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 10px;
        @media(min-width: 992px){
            grid-template-columns: repeat(4, 1fr);
            grid-gap: 20px;
        }
        @media(min-width: 1200px){
            margin: 0 auto;
            width: 1200px;
        }
        .product{
            border: 1px solid #f2f2f2;
            padding: 15px;
            text-decoration: none;
            img{
                max-width: 100%;
            }
            h3{
                font-weight: normal;
                color: var(--blue);
                font-size: 13px;
                min-height: 40px;
                @media(min-width: 768px){
                    font-size: 16px;
                }
            }
            .old-price{
                font-size: 14px;
                text-decoration: line-through;
                color: grey;
                @media(min-width: 768px){
                    font-size: 16px;
                }
            }
            .price{
                font-weight: bold;
                color: var(--blue);
                @media(min-width: 768px){
                    font-size: 18px;
                }
            }
        }
    }
}

</style>