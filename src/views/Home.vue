<template>
  <div class="home">
   <!--  <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    
    <HeaderShayna /> 
    <!-- <h3 v-if="customer"> Hi, {{customer.name}}</h3> -->
    <HeroShayna />
    <WomanShayna />
    <InstaShayna />
    <PartnerShayna />
    <FooterShayna />

    

  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import HeaderShayna from '@/components/HeaderShayna.vue'
import HeroShayna from '@/components/HeroShayna.vue'
import WomanShayna from '@/components/WomanShayna.vue'
import InstaShayna from '@/components/InstaShayna.vue'
import PartnerShayna from '@/components/PartnerShayna.vue'
import FooterShayna from '@/components/FooterShayna.vue'
// import axios from "axios";


export default {
    name: 'Home',
    // data()
    // { 
    //     return{
          
    //         customer: null, 
    //     }
    // },
    // async created()
    // {
    //   const response = await axios.get('customer');
    //   // const response = await axios.get('customer',{
    //   //     headers: {
    //   //       Authorization: 'Bearer' + localStorage.getItem('token')
    //   //     }
    //   // });
    //     this.customer = response.data;
    //   // console.log(response);
    // },
    components: 
    {
        HeaderShayna,
        HeroShayna,
        WomanShayna,
        InstaShayna,
        PartnerShayna,
        FooterShayna
    },
}
</script>
