<template>
    <form @submit.prevent class="input-form">
        <div class="input-field-container">  
            <input 
                v-model="product.name"
                type="text" 
                placeholder="Name" 
                class="input-field"
            >
            <input 
                v-model="product.cost"
                type="text" 
                placeholder="Cost" 
                class="input-field"
            >
            <input 
                v-model="product.code"
                type="text" 
                placeholder="Code" 
                class="input-field"
            >
        </div>
        <form-button
            class="add-button"
            @click="submitForm"
        >Add</form-button>
    </form>
</template>

<script>
import axios from 'axios';
import FormButton from './UI/FormButton.vue';

export default {
    components: { FormButton },
    data() {
        return {
            product: {
                name: '',
                cost: '',
                code: ''
            }
        }
    },
    methods: {
        addProduct() {
            this.id = Date.now()
            this.$emit('create', this.product)
            this.product = {
                name: '',
                cost: '',
                code: ''
            }
        },
        //Sending data to server
        submitForm() {
            axios.post('http://url/api/data', this.formData)
            .then(() => {
                this.formData = {
                name: '',
                cost: 0,
                qrCode: ''
                };
            })
            .catch(error => {
                console.error('Error sending data:', error);
            });
        }
    }
    
}
</script>

<style scoped>
.input-form {
    display: flex;
    align-items: center;
    justify-content: center;
    max-width: 100%;
}
.input-field-container {
    display: flex;
    flex-direction: column;
    max-width: 40%;
}
.input-field {
    margin: 5px;
    padding: 2px 0;
}
.add-button {
    padding: 4px 20px;
}
</style>