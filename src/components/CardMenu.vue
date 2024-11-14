<template>
    <router-link class="text-decoration-none text-dark" to="food">
        <div class="card shadow-sm border-custom text-center border-bottom-1">
            <img :src="require(`@/assets/imgs/${product.gambar}`)"
                class="rounded-top rounded gambar" alt="{{ product.nama}}">
            <div class="card-body">
                <h5 class="card-title">{{ product.nama }}</h5>
                <p class="card-text"> Harga : <i class="bi bi-currency-bitcoin"></i>{{
                    product.harga }}
                </p>
                <a href="#" class="btn btn-info">
                    <i class="bi bi-bag-plus"></i>
                </a>
            </div>
        </div>
    </router-link>
</template>

<script>
export default {
    name: "CardMenuC",
    // cara 1
    // props: {
    //     product: String
    // }
    // cara 2
    props: ['product']

}
</script>

<style></style>