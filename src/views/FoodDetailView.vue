<template>
    <div>
        <NavbarC />
        <div class="container">
            <div class="row col-12 ">
                <nav aria-label="breadcrumb">
                    <ol class="breadcrumb d-none d-lg-inline-flex ">
                        <li class="breadcrumb-item">
                            <RouterLink class="text-decoration-none" to="/">Home</RouterLink>
                        </li>
                        <li class="breadcrumb-item">
                            <RouterLink class="text-decoration-none" to="/food">Food List
                            </RouterLink>
                        </li>
                        <li class="breadcrumb-item active text-decoration-none" aria-current="page">
                            <strong>
                                {{ product.nama }}
                            </strong>
                        </li>
                    </ol>
                </nav>
            </div>
            <div class="row">
                <h2 class="d-block d-md-none container-fluid">
                    <strong>{{ product.nama ? product.nama : 'Sate Ayam' }}</strong>
                </h2>
                <div class="col-12 col-md-6">
                    <p>
                        <img :src="require(`../assets/imgs/${product.gambar ? product.gambar : 'sate-ayam.jpg'}`)"
                            loading="lazy" alt="" class="img-fluid rounded shadow ">
                    </p>
                </div>
                <div class="col-12 col-md-6">
                    <form v-on:submit.prevent>
                        <h2 class="d-none d-md-block">
                            <strong>{{ product.nama ? product.nama : 'Sate Ayam' }}</strong>
                        </h2>
                        <hr>
                        <h4 class="text-info my-2">Harga : <i
                                class="bi bi-currency-bitcoin"></i><strong>{{
                                    product.harga ? product.harga : 'Rp. -' }}</strong> </h4>
                        <div class="form-group">
                            <label for="JumlahPesan">Jumlah Pesan</label>
                            <input type="number" min="0" max="10" v-model="pesan.jumlah_pemesanan"
                                class="form-control" id="JumlahPesan" placeholder="Jumlah Pesan">
                        </div>
                        <div class="form-group">
                            <label for="keterangan">Keterangan Tambahan</label>
                            <textarea v-model="pesan.keterangan" class="form-control"
                                id="keterangan"
                                placeholder="Keterangan: Pedes, Cepat, Nasi Setengah, dll"
                                rows="5"></textarea>
                        </div>

                        <button type="submit" @click="tambahKeranjang" class="btn btn-info"> <i
                                class="bi bi-cart2"></i> Pesan</button>
                    </form>
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
            pesan: {}
        }
    },
    methods: {
        getProduct(data) {
            this.product = data
        },
        tambahKeranjang() {
            if (!this.pesan.jumlah_pemesanan) {
                this.$toast.error('kamu belum mengisi jumlah', {
                    timeout: 5000,
                    position: 'top-right',
                    type: 'error',
                    icon: 'times-circle',
                    iconPack: 'fontawesome',
                    progressBar: true,
                    showMethod: 'slideDown',
                    hideMethod: 'slideUp',
                    dismissible: true,

                })
            } else {
                this.pesan.products = this.product
                axios.post("http://localhost:3000/keranjangs", this.pesan)
                    .then(() => this.pesan.jumlah_pemesanan = 0)
                    // .then(() => this.$router.push("/keranjang"))
                    .then(() => {
                        this.$toast.success(`Berhasil Menambahkan ${this.product.nama}`, {
                            timeout: 2000,
                            position: 'top-right',
                            type: 'success',
                            icon: 'check-circle',
                            iconPack: 'fontawesome',
                            progressBar: true,
                            showMethod: 'slideDown',
                            hideMethod: 'slideUp'

                        })
                    })
                    .catch((x) => {
                        this.$toast.error('error: ' + x, {
                            timeout: 2000,
                            position: 'top-right',
                            type: 'error',
                            icon: 'times-circle',
                            iconPack: 'fontawesome',
                            progressBar: true,
                            showMethod: 'slideDown',
                            hideMethod: 'slideUp',
                        })
                    });
            }

        }
    },
    mounted() {
        axios.get("http://localhost:3000/products/" + this.$route.params.id)
            .then((response) => this.getProduct(response.data))
            .catch((error) => console.log(error));
    }
}
</script>
<style></style>