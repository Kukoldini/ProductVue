<template>
    <div class="product-list">
        <h3>Product list</h3>
        <button
            @click="fetchPosts"
        >Fetch</button>
        <product-item 
            v-for="product in products" 
            :key="product.id"
            :product="product"
        />
    </div>
</template>   

<script>
import ProductItem from '@/components/ProductItem.vue';
import axios from 'axios';

export default {
    components: {
        ProductItem
    },

    data() {
        return {
            products: []
        }
    },

    methods: {
        async fetchPosts() {
            try {
                const response = await axios.get('https://dummyjson.com/products');
                this.products = response.data.products;
            } catch(e) {
                console.log("Error")
            }
        }
    }

}
</script>

<style scoped>
.product-list {
    max-width: 512px;
    margin: 0 auto;
}
</style>