<template>
    <div class="flex flex-col my-4 px-4 py-1">
        <div class="h-32">
        <img :src="product.image" alt="" class="h-full w-full object-cover">
        </div>
        <div>
            <h4 class="text-center py-2">{{product.name}}</h4>
        </div>
        <div>
            <h5 class="text-center py-2 text-gray-600"> €{{ Number(product.price).toFixed(2)}}</h5>
        </div>
        <div class="flex justify-center">
            <button :disabled="isInCart" @click="$emit('add-to-cart', product)" class="bg-green-400 hover:bg-green-600 py-1 px-4 text-gray-100 rounded-lg text-center">
            {{isInCart ? 'Already in Cart' : 'Add to Cart'}}
            </button>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['product', 'isInCart'],

    }
</script>