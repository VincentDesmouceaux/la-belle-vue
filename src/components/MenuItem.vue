
<template>
  <div class="menu-item">
    <img class="menu-item__image" :src="image.source" :alt="image.alt" />
    <div>
      <h3>{{ name }}</h3>
      <p>Price: {{ generatedPrice }} <span v-if="onSale">(10% off!)</span></p>
      <p v-if="inStock">In Stock</p>
      <p v-else>Out of Stock</p>
      <div>
        <label for="add-item-quantity">Quantity: {{ localQuantity }}</label>
        <input v-model.number="localQuantity" id="add-item-quantity" type="number" />
        <BaseButton v-on="$attrs" @click="updateShoppingCart(quantity)">
             Add to shopping cart
         </BaseButton>

      </div>
    </div>
  </div>
</template>

<script>
import BaseButton from './BaseButton.vue'
import { mapActions } from 'vuex'


export default {
  name: 'MenuItem',
  components: {
    BaseButton
  },
  props: {
    
    image: {
      type: Object,
      required: true
    },
    inStock: {
      type: Boolean,
      required: true
    },
    name: {
      type: String,
      required: true
    },
    price: {
      type: Number,
      required: true
    },
    quantity: {
      type: Number,
      defaut: 1
    }
  },
  data() {
    return {
      onSale: false,
      localQuantity: this.quantity
    };
  },
  computed: {
    generatedPrice() {
      if (this.onSale) {
        return (this.price * 0.9).toFixed(2);
      } else {
        return this.price.toFixed(2);
      }
    }
  },
  methods: {
     ...mapActions(['updateShoppingCart'])
    
  },

  beforeMount() {
    const today = new Date().getDate();

    if (today % 2 === 0) {
      this.onSale = true;
    }
  }
};
</script>

<style lang="scss">
.menu-item {
  display: flex;
  width: 500px;
  justify-content: space-between;
  margin-bottom: 30px;

  &__image {
    max-width: 300px;
  }
}
</style>
