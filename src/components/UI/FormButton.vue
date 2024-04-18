<template>
    <button class="button">
        <slot></slot>
    </button>
</template>

<script>
</script>

<style scoped>
.button {
    cursor: pointer;
    border: 1px solid #000;
    border-radius: 4px;
    padding: 2px 6px;
}
.button:hover {
    background-color: #e1dddd;
}
</style>
