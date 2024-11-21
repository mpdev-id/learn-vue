<template>
    <div>
        <NavbarC :propsUpdateKeranjangs="keranjangs" />
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
                                Order
                            </strong>
                        </li>
                    </ol>
                </nav>
            </div>

            <div class="col-12">

            <h1>{{ keranjangs.length }} jenis makanan </h1>
            <div class="table table-responsive table-hover">

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
                        <tr class="align-middle" v-for="(keranjang, index) in keranjangs" :key="keranjang.id">
                            <td>{{ index + 1 }}</td>
                            <td width="150px">
                                <img class="rounded-lg w-100 shadow" loading="lazy"
                                    :src="require(`../assets/imgs/${keranjang.products.gambar ? keranjang.products.gambar : 'sate-ayam.jpg'}`)">
                            </td>
                            <td >{{ keranjang.products.nama }}</td>
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
                                <button class="btn btn-danger" @click="hapusKeranjang(keranjang.id)">
                                    <i class="bi bi-trash"></i>
                                </button>
                            </td>
                        </tr>
                    </tbody>

                    <tr>
                        <td colspan="5" class="text-right">
                            <strong>Total Harga</strong>
                        </td>
                        <td colspan="3" >
                            <strong>Rp.{{ totalHarga }}</strong>
                        </td>
                    </tr>

                </table>
            </div>
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
        },
        hapusKeranjang(id) {
            if (confirm("Apakah anda yakin ingin menghapus data ini ?")) {
                axios
                    .delete(`http://localhost:3000/keranjangs/${id}`)
                    .then(() => this.$router.go())
                    .catch((error) => console.log(error));
                
            }
        }
    },
    
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
