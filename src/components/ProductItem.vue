<template>
    <ul class="product-list-item">
        <li>{{ product.id }}</li>
        <li>{{ product.title }}</li>
        <li>{{ product.price }} RU</li>
        <li>{{ product.brand }}</li>
    </ul>
</template>

<script>
export default {
    props: {
        product: {
            type: Object,
            required: true
        }
    }
}
</script>

<style scoped>
.product-list-item {
    border: 2px solid #b5acac;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 2px 12px;
    margin: 4px auto;
}
li {
    display: flex;
    align-self: flex-start;
}
</style>