<template>
    <div class="receipt-container">
        <select
            v-model="selectedProductId"
            @change="updateSelectedProductId"
        >
            <option value="default" disabled>Select product</option>
            <option 
                v-for="product in products" 
                :key="product.id" 
                :value="product.id"
            >{{ product.title }}</option>
        </select>
            <div class="receipt-nav">
                <span v-if="selectedProducts.length !== 0">Current receipt:</span>
                <span v-else>No product selected</span>
                <form-button
                @click="sendReceipt"
            >Send receipt</form-button>
            </div>
        <product-item
            :product="selectedProduct"
            v-for="selectedProduct in selectedProducts" :key="selectedProduct.id"
        />
    </div>
</template>

<script>
import axios from 'axios'
import ProductItem from '@/components/ProductItem.vue'
import FormButton from '@/components/UI/FormButton.vue';

export default {
    components: {ProductItem, FormButton},

    //Товары в селекте, выбранная опция селекта, товары актуального чека
    data() {
        return {
            products: [],
            selectedProductId: 'default',
            selectedProducts: []
        }
    },
    created() {
        this.fetchData();
    },

    methods: {
        //Запрос на товары в селекте
        async fetchData() {
            try{
                const response = await axios.get('https://dummyjson.com/products');
                this.products = response.data.products;
            } catch(error) {
                console.error(error);
            }
        },
        //Добавление товара в актуальный чек
        updateSelectedProductId() {
            const selectedProduct = this.products.find(p => p.id === this.selectedProductId);
            this.selectedProducts.push(selectedProduct);
        },
        //Отправка чека на сервер
        sendReceipt() {
            axios.post('http://url/api/data', this.formData)
            .then(() => {
                const array = []
                selectedProducts = array;
            })
            .catch(error => {
                console.error('Error sending data:', error);
            });
        }
    }
}

</script>

<style scoped>
.receipt-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    max-width: 512px;
    margin: 0 auto;  
}
.receipt-nav {
    width: 100%;
    margin: 20px auto;
    display: flex;
    justify-content: space-between;
}
</style>