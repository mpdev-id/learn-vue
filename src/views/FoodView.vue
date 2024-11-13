<template>
    <div>
        <NavbarC />
        <div class="container">

            <div class="row p-2 justify-content-center">
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
        };
    },

    methods: {
        setProducts(data) {
            this.products = data
        }
    },

    mounted() {
        axios
            .get("http://192.168.100.80:3000/products")
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
