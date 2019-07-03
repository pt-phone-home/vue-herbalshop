<template>
  <div id="app">
    <navigation-bar :cart="cart" class="z-30"></navigation-bar>
    <hero></hero>
    <div class="container flex flex-wrap" id="shop">
        <div class="w-full lg:w-1/2 flex flex-wrap justify-between">
            <div :key="product.id" class="w-full md:w-1/2" v-for="product in products">
              <product :product="product" :isInCart="isInCart(product)" v-on:add-to-cart="addToCart(product)"></product>
            </div>
        </div>

        <div class="w-full lg:w-1/2">
          <cart :items="cart" v-on:remove-from-cart="removeFromCart($event)" v-on:decrease-order-count="decreaseOrderCount" v-on:increase-order-count="increaseOrderCount" v-on:pay="pay"></cart>
        </div>
    </div>
    
  </div>
</template>

<script>
import NavigationBar from './components/NavigationBar.vue'
import Hero from './components/Hero.vue'
import HelloWorld from './components/HelloWorld.vue'
import Product from './components/Product.vue'
import Cart from './components/Cart.vue'

export default {
  name: 'app',
  components: {
    HelloWorld,
    NavigationBar,
    Hero,
    Product,
    Cart,
  }, 
  data () {
    return {
      products: [
        {'id': 1, 
        'name': 'Lavendar Soap', 
        'price': 5.60,
        'orderCount' :1,
        'image': 'https://res.cloudinary.com/www-rocketchipwebsolutions-ie/image/upload/v1562084611/lavender-2443210_640_zuyhk0.jpg'}, 
      {
        'id' : 2,
        'name' : 'Sage Moisturiser',
        'price' : 9.99,
        'orderCount': 1,
        'image' : 'https://res.cloudinary.com/www-rocketchipwebsolutions-ie/image/upload/v1562097935/glass-3141865_640_dimsqi.jpg',
      },
      {
       'id': 3, 
        'name': 'Probiotic Powder', 
        'price': 35.10, 
        'orderCount': 1,
        'image': 'https://res.cloudinary.com/www-rocketchipwebsolutions-ie/image/upload/v1562098072/essential-oils-1433694_640_p8cuxt.jpg' 
      }, 
      {
        'id': 4, 
        'name': 'Vitamic C Capsules', 
        'price': 12.50, 
        'orderCount': 1,
        'image': 'https://res.cloudinary.com/www-rocketchipwebsolutions-ie/image/upload/v1562098327/pill-3069032_640_hteycu.jpg' 
      }],
      cart: [],
    }
  }, 
  methods: {
    addToCart: function (product) {
      this.cart.push(product);
    }, 
    isInCart: function (product) {
      const item = this.cart.find(item => item.id === product.id);

      if (item) {
        return true
      }
      return false
    },
    removeFromCart: function (product) {
      this.cart = this.cart.filter(item => item.id !== product.id)
    },
    pay: function() {
      if(this.cart.length === 0 ) {
        alert('Please add some items to your shoping cart')
      } else {
        alert('Thank you for shopping with us')
        this.cart = [];
      }
    },
    decreaseOrderCount: function (order) {
      
      order.orderCount--;

    }, 
    increaseOrderCount: function (order) {
      order.orderCount++;
    }
    
  }
}
</script>

<style>

</style>
