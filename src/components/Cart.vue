<template>
    <div class="mt-8">
        <div class="container mx-auto">
            <h2 class="w-full text-center py-2 text-lg border-b-2 border-green-400">Your Shopping Cart</h2>
        </div>
    <div class="w-full flex justify-between py-2 mt-2 bg-gray-200 px-0 sm:px-2" v-for="item in items" :key="item.id">
        
        <div class="w-2/6 text-sm md:text-base">
           {{item.name}} - €{{Number(item.price).toFixed(2)}}
        </div>
        <div class="flex justify-center items-cetner w-1/6">
            
            <button @click="$emit('decrease-order-count', item)" class="mr-2 px-2 rounded bg-green-400 text-gray-100 text-base md:text-lg self-center">-</button>
            <span class="text-sm md:text-base self-center">{{item.orderCount}}</span>
            <button @click="$emit('increase-order-count', item)" class="ml-2 px-2 rounded bg-green-400 text-gray-100 text-base md:text-lg self-center">+</button>
        </div>
        <div class="w-1/6 text-center text-sm md:text-base flex justify-center items-center">
            €{{Number(item.orderCount * item.price).toFixed(2)}}
            
        </div>
        <div class="w-1/6 flex justify-center items-center">
            <button @click="$emit('remove-from-cart', item)" class="bg-red-600 hover:bg-red-400 px-1 text-gray-100 rounded-lg py-1 text-sm md:text-base">X</button>
        </div>
    </div>
    <div class="text-center text-lg md:text-2xl bg-gray-400 mt-4 py-2">
       Total: € {{Number(total).toFixed(2)}}
    </div>

    <div class="flex justify-center">
        <button @click="$emit('pay')" class="bg-green-400 hover:bg-green-600 text-gray-100 text-lg px-2 py-1 rounded mt-4">Pay Now</button>
    </div>
</div>
</template>

<script>
    export default {
        props: ['items'],
        data () {
            return {
                productCount: 1,
            }
        }, 
        methods: {

        },
        computed: {
            total: function () {
                return this.items.reduce((acc, item) => acc + Number(item.price * item.orderCount), 0);
            }
        }
    }
</script>