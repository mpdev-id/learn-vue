<template>
    <NavbarC />
    <div class="container">
        <!-- HERO -->
        <HeroC />
        <!-- FOR YOU -->
        <div class="m-1 p-2 shadow-xl row rounded-lg text-white align-items-center">
            <div class="col-6">
                <strong>
                    For You
                    <i class="bi bi-star"></i>
                </strong>
            </div>
            <div class="col-6">
                <router-link to="food" class="btn btn-light float-right">
                    <i class="bi bi-menu-app"></i>
                </router-link>
            </div>
        </div>
        <!-- card for you -->
        <div class="row p-2">
            <div class=" col-md-3 col-6" v-for="product in products" :key="product.id">
                <CardMenuC :product="product" />
            </div>
        </div>
    </div>
</template>

<script>
// @ is an alias to /src
import HeroC from "@/components/Hero.vue";
import NavbarC from "@/components/Navbar.vue";
import CardMenuC from "@/components/CardMenu.vue";
import axios from "axios";


export default {
    name: "HomeView",
    components: {
        NavbarC,
        HeroC,
        CardMenuC,
    },

    data() {
        return {
            products: [],
        };
    },

    methods: {
        setProducts(data) {
            this.products = data
        }
    },

    mounted() {
        axios
            .get("http://localhost:3000/best-products")
            .then((response) => {
                // console.log(response);
                this.setProducts(response.data);
            })
            .catch((error) => {
                console.log(error);
            });
    },




};
</script>
