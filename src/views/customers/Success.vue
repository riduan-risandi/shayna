<template>
    <div class="success"> 
      
        <div class="d-flex success-checkout align-items-center justify-content-center">
            <div class="col col-lg-4 text-center">
                <img src="img/success-regist.png" alt="" width="294">
                <h3 class="mt-4">
                    Pendaftaran Akun Berhasil!
                </h3>
                
                <p class="mt-2">
                    Silakan login pada link dibawah ini.
                </p>
                <router-link to="/login"><a href="#" class="primary-btn pd-cart mt-3">Login</a></router-link>
            </div>
        </div>

    </div>
</template>


<script> 
  

 export default {
    name: "RegistrationSuccessful"
    
 }
</script>
