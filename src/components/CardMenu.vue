<template>
    <div class="card shadow-sm border-0 border-custom text-center">
        <img :src="require(`@/assets/imgs/${product.gambar}`)" class="rounded-top rounded"
            alt="{{ product.nama}}">
        <div class="card-body">
            <h5 class="card-title">{{ product.nama ?? "" }}</h5>
            <p class="card-text"> Harga : <i class="bi bi-currency-bitcoin"></i>{{
                product.harga }}
            </p>
            <a href="#" class="btn btn-primary">Choose <i class="bi bi-handbag"></i> </a>
        </div>
    </div>
</template>

<script>
export default {
    name: "CardMenuC",
    // props: {
    //     product: String
    // }
    props: ['product']

}
</script>

<style></style>