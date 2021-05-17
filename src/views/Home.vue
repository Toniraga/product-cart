<template>
  <div class="home">
    <ProductDescriptionDrawer
      :product="product"
      :active="active.product_drawer"
      v-on:close-drawer="closeProduct()"
    />
    <div class="product-cards-container">
      <ProductSummaryCard
        v-for="product in items"
        :key="product.id"
        :product='product'
        v-on:view-product="viewProduct($event)"
      />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import items from '../data/items';
import ProductSummaryCard from '../components/products/ProductSummaryCard';
import ProductDescriptionDrawer from '../components/products/ProductDescriptionDrawer';

export default {
  name: 'Home',
  components: {
    ProductSummaryCard,
    ProductDescriptionDrawer
  },
  data () {
    return {
      items,
      product: null,
      active: {
        product_drawer: false
      }
    }
  },
  methods: {
    viewProduct(product) {
      this.product = product
      this.active.product_drawer = true
      console.log(this.product)
    },
    
    closeProduct() {
      this.active.product_drawer = false
    }
  }
}
</script>

<style lang="scss" scoped>
  .product-cards-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }
</style>
