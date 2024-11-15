<template>
    <div>
        <NavbarC />
        <div class="container">
            <div class="row p-2  col-12 ">
                <nav aria-label="breadcrumb">
                    <ol class="breadcrumb">
                        <li class="breadcrumb-item">
                            <RouterLink to="/">Home</RouterLink>
                        </li>
                        <li class="breadcrumb-item">
                            <RouterLink to="/food">Food List</RouterLink>
                        </li>
                        <li class="breadcrumb-item active" aria-current="page">{{ product.nama }}</li>
                    </ol>
                </nav>
            </div>
            <div class="row">
                <div class="col-12 col-md-6">
                    <h2>
                        Menu <strong>{{ product.nama }}</strong>
                    </h2>
                    <img class="w-100" :src="require(`@/assets/imgs/${product.gambar}`)" alt="Hero"  />
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import NavbarC from "@/components/Navbar.vue";
import axios from "axios";
export default {
    name: "FoodDetailView",
    components: {
        NavbarC,
    },
    data() {
        return {
            product: {},
        }
    },
    methods: {
        getProduct(data) {
            this.product = data
        }
    },
    mounted() {
        axios.get(`http://localhost:1000/products/${this.$route.params.id}`).then((response) => {
            this.getProduct(response.data)
        })
    }
}
</script>
<style></style>