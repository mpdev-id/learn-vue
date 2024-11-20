<template>
    <nav class="navbar navbar-expand-lg shadow-sm py-3">
        <div class="container">
            <router-link to="/" class="navbar-brand">
                <img src="@/assets/logo.png" alt="" srcset="@/assets/logo.png" class="w-25 h-25" />
            </router-link>
            <button class="navbar-toggler" type="button" data-toggle="collapse"
                data-target="#navbarScroll" aria-controls="navbarScroll" aria-expanded="false"
                aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarScroll">
                <ul class="navbar-nav mr-auto my-2 my-lg-0 navbar-nav-scroll"
                    style="max-height: 100px">
                    <li class="nav-item">
                        <!-- <h5>Pesan Antar Sekarang</h5> -->
                    </li>
                </ul>

                <ul class="navbar-nav mr-0 my-2 my-lg-0 navbar-nav-scroll"
                    style="max-height: 100px">
                    <li class="nav-item">
                        <router-link to="/food" class="nav-link">
                            <i class="bi bi-ui-radios-grid"></i>
                            Food List
                        </router-link>
                    </li>
                    <li class="nav-item">
                        <router-link to="/order" class="nav-link">
                            <i class="bi bi-cart-x"></i>
                            Order
                            <div class="badge badge-info rounded-circle">{{
                                keranjang.length }}</div>
                        </router-link>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
</template>

<script>
import axios from 'axios';
export default {
    name: "NavbarC",

    data() {
        return {
            keranjang: [],
        }
    },
    methods: {
        setKeranjang(data) {
            this.keranjang = data;
        }
    },
    mounted() {
        axios
            .get("http://localhost:3000/keranjangs")
            .then((response) => this.setKeranjang(response.data))
            .catch((error) => console.log(error));
    }
};
</script>

<style></style>
