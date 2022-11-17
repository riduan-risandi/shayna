<template>
    <div class="shopping">
   <!--  <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    
    <HeaderShayna />  
    <!-- Breadcrumb Section Begin -->
    <div class="breacrumb-section text-left">
        <div class="container">
            <div class="row">
                <div class="col-lg-12">
                    <div class="breadcrumb-text product-more">
                        <router-link to="/"><i class="fa fa-home"></i> Home</router-link>
                        <span>Shopping Cart</span>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <!-- Breadcrumb Section Begin -->

     <!-- Shopping Cart Section Begin -->
    <section class="shopping-cart spad">
        <div class="container">
            <div class="row">
                <div class="col-lg-8">
                    <div class="row">
                        <div class="col-lg-12">
                            <div class="cart-table">
                                <table>
                                    <thead>
                                        <tr>
                                            <th>Image</th>
                                            <th class="p-name text-center">Product Name</th>
                                            <th>Price</th>
                                            <th>Action</th>
                                        </tr>
                                    </thead>
                                    <tbody>
                                        <tr  v-for="keranjang in keranjangUser" :key="keranjang.id">
                                            <td class="cart-pic first-row">
                                                <img class="img-cart" :src="keranjang.photo" />
                                            </td>
                                            <td class="cart-title first-row text-center">
                                                <h5>{{keranjang.name}}</h5>
                                            </td>
                                            <td class="p-price first-row"><small>Rp</small>{{keranjang.price}}</td>
                                            <td @click="removeItem(keranjang.id)" class="delete-item">
                                                <a href="#">
                                                    <i class="material-icons">close</i>
                                                </a>
                                            </td>
                                        </tr> 
                                    </tbody>
                                </table>
                            </div>
                        </div>
                        <div class="col-lg-8">
                            <h4 class="mb-4 text-left">
                                Informasi Pembeli:
                            </h4>
                            <div class="user-checkout text-left" >
                                <form>
                                    <div class="form-group">
                                        <label for="namaLengkap">Nama lengkap</label>
                                        <input type="text" class="form-control" id="namaLengkap" aria-describedby="namaHelp" placeholder="Masukan Nama" v-model="customerInfo.name">
                                    </div>
                                    <div class="form-group">
                                        <label for="namaLengkap">Email Address</label>
                                        <input type="email" class="form-control" id="emailAddress" aria-describedby="emailHelp" placeholder="Masukan Email" v-model="customerInfo.email">
                                    </div>
                                    <div class="form-group">
                                        <label for="namaLengkap">No. HP</label>
                                        <input type="text" class="form-control" id="noHP" aria-describedby="noHPHelp" placeholder="Masukan No. HP" v-model="customerInfo.number">
                                    </div>
                                    
                                        <!-- <select id="provinces"> -->
                                        <!-- <select   class="form-control" id="provinces" @change="onChange($event)">
                                            <option>-- Pilih Provinsi -- </option>
                                            <option  v-for="province in provinces" :key="province.id">{{province}}</option> 
                                        </select>  -->

                                        <!-- <select  id="provinces">
                                            <option v-for="person in provinces" v-bind:value="key">
                                            {{ person.name }}
                                            </option>
                                        </select> -->

                                    <div class="form-group">
                                        <label for="provinsi">Provinsi</label> 
                                        <select   class="form-control" id="provinces" @change="changeProvince($event)">
                                            <option>-- Pilih Provinsi -- </option>
                                            
                                            <option  v-for="province in provinces" :key="province.province_id" :value="province.province_id">{{province.title}}</option> 
                                        </select> 

                                    </div> 
                                    <div class="form-group">
                                        <label for="kota">Kota</label>  
                                        <select   class="form-control" id="cities"  v-model="cities_id">
                                            <option>-- Pilih Kota -- </option>
                                            <option  v-for="city in cities" :key="city.city_id" :value="city.city_id">{{city.title}}</option> 
                                        </select> 
 
                                    </div> 
                                    <div class="form-group">
                                        <label for="kurir">Kurir</label>  
                                        <select   class="form-control" id="couriers" @change="changeCourier($event)">
                                            <option>-- Pilih Kurir -- </option>
                                            <option  v-for="courier in couriers" :key="courier.code" :value="courier.code">{{courier.title}}</option> 
                                        </select> 
 
                                    </div> 
                                    <div class="form-group">
                                        <label for="kurir">Ongkos Kirim</label>  
                                        <select   class="form-control" id="ongkirs">
                                            <option>-- Silahkan Pilih -- </option>
                                            <option  v-for="ongkir in ongkirs" :key="ongkir.cost" :value="ongkir.cost">{{ongkir.fullname}}</option> 
                                        </select> 
 
                                    </div> 
                                    <div class="form-group">
                                        <label for="alamatLengkap">Alamat Lengkap</label>
                                        <textarea class="form-control" id="alamatLengkap" rows="3" v-model="customerInfo.address"></textarea>
                                    </div>
                                </form>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="col-lg-4">
                    <div class="row">
                        <div class="col-lg-12">
                            <div class="proceed-checkout text-left">
                                <ul>
                                    <li class="subtotal">ID Transaction <span>#SH12000</span></li>
                                    <li class="subtotal mt-3">Subtotal <span><small>Rp</small>{{totalHarga}}</span></li>
                                    <li class="subtotal mt-3">Pajak <span>10% {{ditambahPajak}}</span></li>
                                    <li class="subtotal mt-3">Total Biaya <span><small>Rp</small>{{totalBiaya}}</span></li>
                                    <li class="subtotal mt-3">Bank Transfer <span>Mandiri</span></li>
                                    <li class="subtotal mt-3">No. Rekening <span>2208 1996 1403</span></li>
                                    <li class="subtotal mt-3">Nama Penerima <span>Shayna</span></li>
                                </ul>
                                <!-- <router-link to="/success"> -->
                                    <a @click="checkout()" href="#" class="proceed-btn">I ALREADY PAID</a>
                                <!-- </router-link> -->
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
    <!-- Shopping Cart Section End -->  

  </div>
</template> 

<script> 

import HeaderShayna from '@/components/HeaderShayna.vue';  
import axios from "axios";

 export default {
    name: "cart",
    components: 
    {
        HeaderShayna  
    },
    data() 
    {
        return{ 
            keranjangUser: [],
            /* keranjangUserTest: [], */
            customerInfo:{
                name:'',
                email:'',
                number:'',
                address:''
            },
            // provinces:{ 
            // }, 
            provinces: [],
            cities: [],
            couriers: [],
            ongkirs: [],
            cities_id:null,
            // provinceAll: [],
            // cities:{}
        }

    },
    methods:{
        // removeItem(index){
        //     this.keranjangUser.splice(index,1);
        //     const parsed = JSON.stringify(this.keranjangUser);
        //     localStorage.setItem('keranjangUser',parsed);
        // },

       /*  setDataPicture(data){
            console.log("TEST");
            console.log(data);
            // replace object productDetails dengan data dari API
            this.keranjangUserTest = data;
            // replace value gambardefault dengan data dari API(galleries)
            // this.gambar_default = data.galleries[0].photo;


        }, */
        setDataProvinces(data)
        {
            // replace object provinceAll dengan data dari API
            this.provinces = data; 
            // console.log(data) 
        },
        setDataCities(data)
        {
            // console.log(data);
            // replace object provinceAll dengan data dari API
            this.cities = data;   
        },
        setDataCouriers(data)
        {
            // replace object provinceAll dengan data dari API
            this.couriers = data;   
        },
        setDataOngkir(data)
        {
            // console.log("masuk");
            // console.log(data);
            // replace object ongkir dengan data dari API
            this.ongkirs = data;   
        },

        removeItem(idx)
        {
             
            // cari tau id dari si item yang akan dihapus
            let keranjangUserStorage = JSON.parse(localStorage.getItem("keranjangUser"));
            let itemKeranjangUserStorage = keranjangUserStorage.map(itemKeranjangUserStorage => itemKeranjangUserStorage.id);

            //cocokkan id item dengan id yg di storage
            let index = itemKeranjangUserStorage.findIndex(id => id == idx);
            this.keranjangUser.splice(index,1);

            const parsed = JSON.stringify(this.keranjangUser);
            localStorage.setItem('keranjangUser',parsed);

            window.location.reload(); 
        },
        checkout()
        {
            let productIds = this.keranjangUser.map(function(product){
                return product.id
            });

            let checkoutData={
                'name' : this.customerInfo.name,
                'email' : this.customerInfo.email,
                'number' : this.customerInfo.number,
                'address' : this.customerInfo.address,
                'transaction_total' : this.totalBiaya,
                'transaction_status' : "PENDING",
                'transaction_detail' : productIds
            };

            axios
                .post(
                    "http://127.0.0.1:8000/api/checkout",checkoutData
                )
                .then(() => this.$router.push("success"))
                //eslint-disable-next-line no-console
                .catch(err => console.log(err));
        },
        changeProvince(event)
        {
            // console.log("masuk")
            // console.log(event.target.value);
            
            axios
            .get("http://127.0.0.1:8000/api/cities",{
                params:{
                    id:event.target.value
                }
            })
            // .then(res=>(this.provinces = res.data.data)) 
            // .then(res=>(console.log(res.data.data)))
            .then(res=>(this.setDataCities(res.data.data)))
            .catch(err=>console.log(err)); 

        },
        changeCourier(event)
        {
            var self = this;  
            axios
            .get("http://127.0.0.1:8000/api/cek_ongkir",{
                params:{
                    courier:event.target.value,
                    city_destination:self.cities_id,
                }
            }) 
            // .then(res=>(console.log(res.data.data)))
            .then(res=>(this.setDataOngkir(res.data.data)))
            .catch(err=>console.log(err)); 

        }

    },
    mounted(){
        if (localStorage.getItem('keranjangUser')){
            try{
                this.keranjangUser= JSON.parse(localStorage.getItem('keranjangUser'));
            } catch(e){
                localStorage.removeItem('keranjangUser');
            }
        }

        axios
            .get("http://127.0.0.1:8000/api/provinces",{
                // params:{
                //     id:this.$route.params.id
                // }
            })
            // .then(res=>(this.provinces = res.data.data)) 
            // .then(res=>(console.log(res.data.data)))
            .then(res=>(this.setDataProvinces(res.data.data)))
            .catch(err=>console.log(err));
            
        axios
            .get("http://127.0.0.1:8000/api/couriers",{
                 
            })
            // .then(res=>(this.provinces = res.data.data)) 
            // .then(res=>(console.log(res.data.data)))
            .then(res=>(this.setDataCouriers(res.data.data)))
            .catch(err=>console.log(err));

        axios
            .get("http://127.0.0.1:8000/api/cek_ongkir",{
                 
            })
            // .then(res=>(this.provinces = res.data.data)) 
            // .then(res=>(console.log(res.data.data)))
            .then(res=>(this.setDataCouriers(res.data.data)))
            .catch(err=>console.log(err));

       /*  axios
            .get("http://127.0.0.1:8000/api/cart",{
                params:{
                    id:this.$route.params.id
                }
            })
            // .then(res=>(this.keranjangUser = res.data.data))
            .then(res=>(this.setDataPicture(res.data.data)))
            // .then(res=>(console.log("test1")))
            .catch(err=>console.log(err)); */
            
    },
     computed:
    {
        totalHarga()
        {
            return this.keranjangUser.reduce(function(items,data){
                // alert(data.price);
                // console.log(data.price)
                return items + data.price;
            },0);
        },
        ditambahPajak()
        {
            return (this.totalHarga * 10) /100;
        },
        totalBiaya()
        {
            return this.totalHarga + this.ditambahPajak 
        }
    }
 }
</script>

<style scoped>
    .img-cart{
        width: 100px;
        height: 100px;;
    }  
</style>