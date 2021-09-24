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
                        <span>Register</span>
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
                        <h2>Register</h2>
                        <!-- <div v-if="errors" class="error-messages">
                            <div v-for="(error, index) in errors" :key="index">
                                <ul>
                                <li>{{ error[0] }}</li>
                                </ul>
                            </div>
                        </div>   -->
                            
                            <!-- <form action="http://minangtech.com/Login" method="post" _lpchecked="1"> -->
                        <!-- <form> -->
                        <!-- <form @submit.prevent="submit"> -->
                        <form @submit.prevent="handleSubmit">
                            <div class="group-input">
                                <label for="name" style="text-align: left;">Nama</label>
                                <input type="text" id="namaLengkap" v-model="customer.name" >
                                <!-- <div v-if="validation.name">{{ validation.name}}</div> -->
                                <div v-if="validation.name" class="mt-2 alert alert-danger">
                                        {{ validation.name[0] }}
                                </div>
                            </div>
                            <div class="group-input">
                                <label for="number" style="text-align: left;">No. Hp</label>
                                <input type="text" id="number" v-model="customer.number" >
                                <div v-if="validation.number" class="mt-2 alert alert-danger">
                                        {{ validation.number[0] }}
                                </div>
                            </div>
                            <div class="group-input">
                                <label for="email" style="text-align: left;">Email</label> 
                                <input type="email" id="email" v-model="customer.email" >
                                <div v-if="validation.email" class="mt-2 alert alert-danger">
                                    {{ validation.email[0] }}
                                </div>
                            </div>
                            <div class="group-input">
                                <label for="password" style="text-align: left;">Password </label> 
                                <input type="password" id="password" v-model="customer.password" >
                                <div v-if="validation.password" class="mt-2 alert alert-danger">
                                    {{ validation.password[0] }}
                                </div>
                            </div>
                            <div class="group-input">
                                <label for="password_confirmation" style="text-align: left;">Konfirmasi Password </label>
                                <input type="password" id="password_confirmation" v-model="customer.password_confirmation" > 
                                <div v-if="validation.password_confirmation" class="mt-2 alert alert-danger">
                                    {{ validation.password_confirmation[0] }}
                                </div>
                            </div>
                            <div class="group-input gi-check">
                                <div class="gi-more">
                                    <!-- <a href="http://minangtech.com/ResetPassword" class="forget-pass">Forget your Password</a> --> 
                                     <a href="#" class="forget-pass gray-text">
                                        <router-link to="/reset_password">Forget your Password</router-link >
                                    </a>
                                </div>
                            </div>
                             <!-- <a @click="checkout()" href="#" class="site-btn login-btn">Register</a> -->
                            <button class="site-btn login-btn">Register</button>
                        </form>
                        <div class="switch-login ">
                            <!-- <a href="http://minangtech.com/Register" class="or-login">Or Create An Account</a>
                            <BR></BR>  -->
                              
                            <a href="#" class="or-login black-text">
                                <router-link to="/login">Or Login</router-link >
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
    name: "register",
    components: 
    {
        HeaderShayna , 
        // RelatedShayna,
        PartnerShayna,
        FooterShayna,
    },
    //     data() {
    // emailError: ""
    // }

    data() 
    {
        return{ 
            validation:  [], 
            // errors: null,
            customer:{
                name:'',
                number:'',
                email:'',
                password:'',
                password_confirmation:''
            }

        }

    },
    methods:{ 
        async handleSubmit()
        {   
            // const data = {
            //     'name' : this.customer.name,
            //     'number' : this.customer.number,
            //     'email' : this.customer.email,
            //     'password' : this.customer.password,
            //     'password_confirmation' : this.customer.password_confirmation,
            // }; 

            // e.preventDefault()
            // axios.post('http://127.0.0.1:8000/api/register',data)
            // axios.post('register',data)
            // .then(
            //     res => {
            //         console.log(res)
            //     }
            // )
            // .catch(
            //     err => {
            //         console.log(err)
            //     }
            // )
             await axios.post('register',{
                'name' : this.customer.name,
                'number' : this.customer.number,
                'email' : this.customer.email,
                'password' : this.customer.password,
                'password_confirmation' : this.customer.password_confirmation,
            });
            
            // console.log(response);
            
                // .then(() => this.$router.push("register/success"))
            this.$router.push('/register/success');
        }
    }, 
 }
</script>

<style scoped> 
    .black-text a {
    color: #252525;
    }
    .gray-text a {
    color: #6B6B6B;
    }
</style> 