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
                        <!-- <form> -->
                        <!-- <form @submit.prevent="handleSubmit"> --> 
                        <form @submit.prevent="handleSubmit">
                            <div class="group-input">
                                <label for="email" style="text-align: left;">Email</label>
                                <!-- <input type="email" id="email" name="email" value=""  > -->
                                <input type="email" id="email" v-model="customer.email" >
                            </div>
                            <div class="group-input">
                                <label for="password" style="text-align: left;">Password </label>
                                <input type="password" id="password" v-model="customer.password" >
                                <!-- <input type="password" id="password" name="password"  > -->
                            </div>
                            <div class="group-input gi-check">
                                <div class="gi-more">
                                    <!-- <a href="http://minangtech.com/ResetPassword" class="forget-pass">Forget your Password</a> --> 
                                     <a href="#" class="forget-pass gray-text">
                                        <router-link to="/reset_password">Forget your Password</router-link >
                                    </a>
                                </div>
                            </div>
                            <button class="site-btn login-btn">Sign In</button>
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
    import PartnerShayna from '@/components/PartnerShayna.vue'
    import FooterShayna from '@/components/FooterShayna.vue';
    
    import axios from "axios"; 

    export default {
        name: "login",
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
                
                customer:{ 
                    email:'',
                    password:'' 
                }

            }

        },
        methods:{ 
            
            async handleSubmit()
            {   
                const response = await axios.post('login',{
                    'email' : this.customer.email,
                    'password' : this.customer.password,
                });
                // console.log(response);

                localStorage.setItem('token',response.data.token);
                // this.$router.go()
                this.$router.push('/')
 
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