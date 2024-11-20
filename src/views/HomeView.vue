<template>
    <div>
        <NavbarC />
        <div class="container">
            <!-- HERO -->
            <HeroC />
            <!-- FOR YOU -->
            <div class="mt-5 p-1 shadow-xl row  align-items-center">
                <div class="col-6">
                    <span class="">
                        Best Seller
                        <i class="bi bi-moon-stars-fill text-info"></i>
                    </span>
                </div>
                <div class="col-6">
                    <router-link to="food" class="btn btn-info btn-lg float-right">
                        <i class="bi bi-menu-app"></i>
                    </router-link>
                </div>
            </div>
            <!-- card for you -->
            <div class="row px-5 py-2 ">

                <!-- cari -->
                <div class=" col-xl-3 col-lg-4 col-md-6 col-12 my-2" v-for="product in products"
                    :key="product.id">
                    <CardMenuC :product="product" />
                </div>
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
                console.error(error);
            });
    },




};
</script>
