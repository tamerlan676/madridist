<template lang="pug">
.main 
  Hero
  Hits
  ProductsWrapper(:collection="collection")
  PayDelivery
  Banner
</template>


<script>
export default {
  async fetch({ store, params }) {
      const options = {
        collectionName: 'Retro'
      }
        await store.dispatch("getCollection", options);
    },
  computed: {
        collection() {
            return this.$store.state.collection;
        }
    }
}
</script>




