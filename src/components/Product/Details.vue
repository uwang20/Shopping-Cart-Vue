<template>
    <div class="product-details">
        <h2 class="product-name">{{ name }}</h2>
    </div>
</template>

<script>
export default {
    name: "Details",
    props: {
        name: {
            type: String,
            required: true
        }
    }
}
</script>

<style scoped>
.product-details{
    padding: 10px;
    flex: 1;

    display: flex;
    flex-direction: column;
}

.product-name{
    font-size: 1.2rem;
}
</style>