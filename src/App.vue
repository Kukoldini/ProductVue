<template>
    <div class="app">
        <product-form
            @create="addProduct"
        />
        <product-list 
            :products="products"
        />
        <receipt-page
            :products="products"
        />
    </div>
</template>

<script>
import ProductForm from '@/components/ProductForm.vue';
import ProductList from '@/components/ProductList.vue';
import ReceiptPage from '@/components/createReceipt/ReceiptPage.vue';

export default {

    components: {
        ProductForm, ProductList, ReceiptPage
    },

    data() {
        return {
            products: []
        }
    },

    methods: {
        addProduct(product) {
            this.products.push(product);
        },
        removeProduct(product) {
            this.products = this.products.filter(p => p.id !== product.id)
        }
    }
}
</script>

<style>

</style>
