<template>
    <div>
        <NavbarC />
        <div class="container">

            <div class="row p-2 justify-content-center col-12 col-md-4 justify-self-end">
                <div class="input-group align-items-center ">
                    <div class="input-group-prepend mr-2">
                        <span class="">Search</span>
                    </div>
                    <input v-model="search" @keypress="searchProduct(search)" placeholder="Search"
                        type="text" aria-label="First name" class="form-control">
                </div>
            </div>

            <div class="row p-2 ">
                <div class=" col-xl-3 col-lg-4 col-md-6 col-12 my-2" v-for="product in products"
                    :key="product.id">
                    <CardMenuC :product="product" />
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import NavbarC from "@/components/Navbar.vue";
import CardMenuC from "@/components/CardMenu.vue";
import axios from "axios";

export default {
    name: "FoodView",
    components: {
        NavbarC,
        CardMenuC
    },


    data() {
        return {
            products: [],
            search: ""
        };
    },

    methods: {
        /**
         * Set products data to component
         * @param {array} data - Array of object products
         */
        setProducts(data) {
            this.products = data
        },
        /**
         * Search product by name
         * @param {string} search
         */
        searchProduct(search) {
            // Get products from API with query parameter
            axios
                .get("http://localhost:1000/products?q=" + search)
                .then((response) => {
                    // Set products data to component
                    this.setProducts(response.data);
                })
                .catch((error) => {
                    console.error(error);
                });
        }
    },

    mounted() {
        axios
            .get("http://localhost:1000/products")
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

<style></style>
