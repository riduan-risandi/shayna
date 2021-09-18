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
                        <span>Login</span>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <!-- Breadcrumb Section Begin -->

    <!-- Login Section Begin -->
    <section class="register-login-section spad"> 
        <div class="container">
            <div class="row">
                <div class="col-lg-6 offset-lg-3">
                    <div class="login-form">
                        <h2>Login</h2>
                            <!-- <form action="http://minangtech.com/Login" method="post" _lpchecked="1"> -->
                            <form>
                            <div class="group-input">
                                <label for="email" style="text-align: left;">Email</label>
                                <input type="email" id="email" name="email" value=""  >
                            </div>
                            <div class="group-input">
                                <label for="password" style="text-align: left;">Password </label>
                                <input type="password" id="password" name="password"  >
                            </div>
                            <div class="group-input gi-check">
                                <div class="gi-more">
                                    <!-- <a href="http://minangtech.com/ResetPassword" class="forget-pass">Forget your Password</a> --> 
                                     <a href="#" class="forget-pass gray-text">
                                        <router-link to="/reset_password">Forget your Password</router-link >
                                    </a>
                                </div>
                            </div>
                            <button type="submit" class="site-btn login-btn">Sign In</button>
                        </form>
                        <div class="switch-login ">
                            <!-- <a href="http://minangtech.com/Register" class="or-login">Or Create An Account</a>
                            <BR></BR>  -->
                              
                            <a href="#" class="or-login black-text">
                                <router-link to="/register">Or Create An Account</router-link >
                            </a>
                                
                        </div>
                    </div>
                </div>
            </div> 
    </div>
    </section>
    
    <!-- Login Section End -->
  
    <!-- <RelatedShayna /> -->
    <PartnerShayna />
    <FooterShayna />

    

  </div>
</template>


<script> 

import HeaderShayna from '@/components/HeaderShayna.vue';  
// import RelatedShayna from '@/components/RelatedShayna.vue';
import PartnerShayna from '@/components/PartnerShayna.vue'
import FooterShayna from '@/components/FooterShayna.vue';
import axios from "axios";

 export default {
    name: "cart",
    components: 
    {
        HeaderShayna , 
        // RelatedShayna,
        PartnerShayna,
        FooterShayna,
    },
    data() 
    {
        return{ 
            keranjangUser: [],
            customerInfo:{
                name:'',
                email:'',
                number:'',
                address:''
            }

        }

    },
    methods:{
        // removeItem(index){
        //     this.keranjangUser.splice(index,1);
        //     const parsed = JSON.stringify(this.keranjangUser);
        //     localStorage.setItem('keranjangUser',parsed);
        // },
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
    },
     computed:
    {

        totalHarga()
        {
            return this.keranjangUser.reduce(function(items,data){
                // alert(items);
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
    .black-text a {
    color: #252525;
    }
    .gray-text a {
    color: #6B6B6B;
    }
</style> 