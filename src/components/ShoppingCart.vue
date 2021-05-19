<template>
    <div @click="showCart = !showCart" class="cart">
        Shopping Cart: {{cart.length}} items
    </div>
            <div class="items" v-if="showCart">
            <ul>
                <li 
                class="ind"
                @click="$emit('remove',item)"
                v-for="item in cart" 
                :key="item">
                    {{item.title}}
                </li>
            </ul>
        </div>
</template>

<script>
    export default {
        props: {
            cart: Array,
        },
        
        data() {
            return {
                showCart: false,
            }
        },
        emits: ['remove'],
        } 
</script>

<style scoped>
.cart{
    position:absolute;
    right:0;
    top:0;
    margin:40px;
    color:white;
    padding:10px;
    background:green;
}
.items{
        color:white;
    padding:10px;
    background:green;
}
.ind {
    margin:20px;
    background:blue;
}
</style>