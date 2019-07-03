<template>
    <div class="w-full flex bg-gray-100 sticky top-0 border-b-2 border-green-200">
        <div class="container mx-auto flex justify-between py-4 items-center  bg-gray-100 ">
            <div class="flex items-center"><img src="https://res.cloudinary.com/www-rocketchipwebsolutions-ie/image/upload/c_scale,w_100/v1562075409/logo_rctz0g.png" alt=""> 
            <p class="pl-4 font-hairline text-base sm:text-lg md:text-2xl lg:text-3xl tracking-wider">Herbal Recipes and Remedies</p></div>
        </div>
        <div class="flex justify-center items-center px-8">
            <p><i class="fas fa-cart-arrow-down text-green-400 text-xl"></i><span class="pl-2 text-gray-600">{{cart.length}}</span></p>
        </div>
    </div>
    
</template>

<script>
    
    export default {
        props: ['cart'],
    }
</script>