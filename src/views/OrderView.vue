<template>
    <div>
        <NavbarC />
        <div class="container">

            <h1>{{ keranjangs.length }} jenis makanan </h1>
            <div class="table table-responsive">

                <table class="table">
                    <thead>
                        <tr>
                            <th>No</th>
                            <th>Gambar</th>
                            <th>Nama</th>
                            <th>Unit</th>
                            <th>harga</th>
                            <th>total harga</th>
                            <th>Keterangan</th>
                            <th>Hapus</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="(keranjang, index) in keranjangs" :key="keranjang.id">
                            <td>{{ index + 1 }}</td>
                            <td width="250px">
                                <img class="rounded-lg w-100 shadow" loading="lazy"
                                    :src="require(`../assets/imgs/${keranjang.products.gambar ? keranjang.products.gambar : 'sate-ayam.jpg'}`)">
                            </td>
                            <td>{{ keranjang.products.nama }}</td>
                            <td>{{ keranjang.jumlah_pemesanan }}</td>
                            <td>Rp.{{ keranjang.products.harga }}</td>
                            <td>
                                Rp.
                                <strong>
                                    {{ keranjang.products.harga * keranjang.jumlah_pemesanan }}
                                </strong>
                            </td>
                            <td>{{ keranjang.keterangan }}</td>
                            <td class="text-center">
                                <i class="bi-trash-fill text-danger hljs-strong">


                                </i>
                            </td>
                        </tr>
                    </tbody>

                    <tr>
                        <td colspan="5" class="text-right">
                            <strong>Total Harga</strong>
                        </td>
                        <td>
                            <strong>Rp.{{ totalHarga }}</strong>
                        </td>
                    </tr>

                </table>
            </div>
        </div>
    </div>
</template>

<script>
import NavbarC from "@/components/Navbar.vue";
import axios from "axios";
export default {
    name: "OrderView",
    components: {
        NavbarC,
    },
    data() {
        return {
            keranjangs: [],

        };
    },
    methods: {
        setKeranjang(data) {
            this.keranjangs = data
        }
    },
    /*************  ✨ Codeium Command ⭐  *************/
    /**
     * Fetches the keranjang data from the server and stores it in the
     * component's `keranjang` data property.
     */
    /******  e78e15a8-b774-4fab-8dbb-785e42c13ee4  *******/
    mounted() {
        axios
            .get("http://localhost:3000/keranjangs")
            .then((response) => this.setKeranjang(response.data))
            .catch((error) => console.log(error));
    },
    computed: {
        totalHarga() {
            let total = 0;
            for (let i = 0; i < this.keranjangs.length; i++) {
                total += this.keranjangs[i].products.harga * this.keranjangs[i].jumlah_pemesanan;
            }
            return total;
        },
    },
};
</script>

<style></style>
