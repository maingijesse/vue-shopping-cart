 <template>
  <div class="container">
    <div class="row">
      <div class="col-md-7">
        <div class="row">
          <div class="col-md-6" v-for="product in products" :key="product.id">
            <product
              :product="product"
              @addToCart="addToCart(product)"
              :isInCart="isInCart(product)"
            ></product>
          </div>
        </div>
      </div>
      <div class="col-md-5 my-5">
        <cart :items="cart" @remove-from-cart="removeFromCart($event)" @pay="clearCart"></cart>
      </div>
    </div>
  </div>
</template>

<script>
import products from "./products";
import Product from "./components/Product";
import Cart from "./components/Cart";
export default {
  data() {
    return {
      products,
      cart: []
    };
  },
  components: {
    Product,
    Cart
  },
  methods: {
    addToCart(product) {
      this.cart.push(product);
    },
    isInCart(product) {
      const item = this.cart.find(item => item.id === product.id);
      if (item) {
        return true;
      }
      return false;
    },
    removeFromCart(product) {
      this.cart = this.cart.filter(item => item.id !== product.id);
    },
    clearCart() {
      this.cart = [];
      alert("payment successful");
    }
  }
};
</script>

<style>
/* cart component 1:44 */
</style>

