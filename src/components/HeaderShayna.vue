<template>
    <div>

        <!-- Header Section Begin -->
        <header class="header-section">
            <div class="header-top">
                <div class="container">
                    <div class="ht-left">
                        <div class="mail-service">
                            <i class="fa fa-envelope"></i>
                            riduanrisandi@gmail.com
                        </div>
                        <div class="phone-service">
                            <i class="fa fa-phone"></i>
                            082213934655
                        </div>
                    </div>
                    <div class="ht-right"> 
                        
                        <a v-if="customer" href="#" class="login-panel header-text">
                            <a href="javascript:void(0)" @click="handleClick"><i class="fa fa-sign-out"></i>Logout</a>
                        </a>
                        <a v-if="customer" class="login-panel header-text">
                          Hi, <b>{{customer.name}} </b>
                        </a>
                        <a v-if="!customer" href="#" class="login-panel header-text">
                            <router-link to="/login"><i class="fa fa-user"></i>Login</router-link>
                        </a>
                        
                        <!-- <h3 v-if="customer"> Hi, {{customer.name}}</h3> -->

                        <div class="lan-selector mr-1 ml-1">
                            <img src="img/indonesia.png" alt="" />
                            Indonesia
                        </div>
                        <div class="top-social">
                            <a href=""><i class="ti-facebook"></i></a>
                            <a href=""><i class="ti-twitter-alt"></i></a>
                            <a href=""><i class="ti-linkedin"></i></a>
                            <a href=""><i class="ti-youtube"></i></a>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="container">
              <!-- <div class="inner-header">
                <div class="row">
                    <div class="col-lg-2 col-md-2">
                        <div class="logo">
                            <a href="http://minangtech.com/">
                                <img src="http://minangtech.com/resource/logo.png" alt="">
                            </a>
                        </div>
                    </div>
                    <div class="col-lg-7 col-md-7">
                        <form action="http://minangtech.com/Shop" method="GET" _lpchecked="1">
                            <div class="advanced-search">
                              <select name="jenis-kategori" id="jenis-kategori" class="category-btn">
                                <option value="man-kaos">Man - Kaos</option>
                                <option value="man-hodie">Man - Hodie</option>
                                <option value="man-sepatu">Man - Sepatu</option>
                                <option value="man-tas">Man - Tas</option>
                                <option value="woman-kaos">Woman - Kaos</option>
                                <option value="woman-hodie">Woman - Hodie</option>
                                <option value="woman-sepatu">Woman - Sepatu</option>
                                <option value="woman-tas">Woman - Tas</option>
                                <option value="kid-kaos">Kid - Kaos</option>
                                <option value="kid-hodie">Kid - Hodie</option>
                                <option value="kid-sepatu">Kid - Sepatu</option>
                                <option value="kid-tas">Kid - Tas</option>
                              </select>
                              <div class="input-group">
                                  <input type="text" name="search" placeholder="What do you need?" value="">
                                  <button type="submit" value="search"><i class="ti-search"></i></button>
                              </div>
                            </div>
                        </form>
                    </div>
                    <div class="col-lg-3 text-right col-md-3">
                        <ul class="nav-right">
                            <li class="cart-icon">
                                <a href="#">
                                    <i class="icon_heart_alt"></i>
                                    <span id="jumlah-wishlist">0</span>
                                </a>
                                <div class="cart-hover">
                                    <div class="select-items">
                                        <table>
                                            <tbody id="data-wishlist"></tbody>
                                        </table>
                                    </div>
                                    <div class="select-total">
                                        
                                    </div>
                                    <div class="select-button">
                                        <a href="http://minangtech.com/Wishlist" class="primary-btn view-card">VIEW Wishlist</a>
                                    </div>
                                </div>
                            </li>
                            <li class="cart-icon">
                                <a href="#">
                                    <i class="icon_bag_alt"></i>
                                    <span class="cart-amunt">0</span>
                                </a>
                                <div class="cart-hover">
                                    <div class="select-items">
                                        <table>
                                            <tbody id="data-pembelian"></tbody>
                                        </table>
                                    </div>
                                    <div class="select-total">
                                        <span>total:</span>
                                        <h5 class="cart-price">Rp. 0</h5>
                                    </div>
                                    <div class="select-button">
                                        <a href="http://minangtech.com/Cart" class="primary-btn view-card">VIEW CARD</a>
                                        <a href="http://minangtech.com/Checkout" class="primary-btn checkout-btn">CHECK OUT</a>
                                    </div>
                                </div>
                            </li>
                            <li class="cart-price">Rp. 0</li>
                        </ul>
                    </div>
                </div>
              </div> -->

                <div class="inner-header">
                    <div class="row">
                        <div class="col-lg-2 col-md-2">
                            <div class="logo">
                                <a href="#">
                                    <router-link to="/"><img src="img/sandi_logo.png" alt="" /></router-link>
                                </a>
                            </div>
                        </div>
                        <div class="col-lg-7 col-md-7"></div>
                        <div class="col-lg-3 text-right col-md-3">
                            <ul class="nav-right">
                                <!-- <li class="cart-icon">
                                    <a href="#">
                                        <i class="icon_heart_alt"></i>
                                        <span id="jumlah-wishlist">0</span>
                                    </a>
                                    <div class="cart-hover">
                                        <div class="select-items">
                                            <table>
                                                <tbody id="data-wishlist"></tbody>
                                            </table>
                                        </div>
                                        <div class="select-total">
                                            
                                        </div>
                                        <div class="select-button">
                                            <a href="javascript:void(0)" class="primary-btn view-card">VIEW Wishlist</a>
                                        </div>
                                    </div>
                                </li> -->

                                <li class="cart-icon">
                                    Keranjang Belanja &nbsp;
                                    <a href="#">
                                        <i class="icon_bag_alt"></i>
                                        <span>{{ keranjangUser.length }}</span>
                                    </a>
                                    <div class="cart-hover">
                                        <div class="select-items">
                                            <table>
                                                <tbody v-if="keranjangUser.length > 0">
                                                    <tr v-for="keranjang in keranjangUser" :key="keranjang.id">
                                                        <td class="si-pic">
                                                            <img class="photo-item" :src="keranjang.photo" alt="" />
                                                        </td>
                                                        <td class="si-text">
                                                            <div class="product-selected">
                                                                <p>Rp{{ keranjang.price }} x 1</p>
                                                                <h6>{{ keranjang.name }}</h6>
                                                            </div>
                                                        </td>
                                                        <td @click="removeItem(keranjang.id)" class="si-close">
                                                            <i class="ti-close"></i>
                                                        </td>
                                                    </tr>
                                                </tbody>
                                                <tbody v-else>
                                                    <tr>
                                                        <td>Keranjang Kosong</td>
                                                    </tr>
                                                </tbody>
                                            </table>
                                        </div>
                                        <div class="select-total">
                                            <span>total:</span>
                                            <h5>Rp{{ totalHarga }}.00</h5>
                                        </div>
                                        <div class="select-button">
                                            <a href="#" class="primary-btn view-card">
                                                <router-link to="/cart" style="color: #fff">VIEW CARD</router-link>
                                            </a>
                                            <a href="#" class="primary-btn checkout-btn">
                                                <router-link to="/cart">CHECK OUT</router-link>
                                            </a>
                                        </div>
                                    </div>
                                </li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
            <div class="nav-item">
                <div class="container">
                    <div class="nav-depart">
                        <div class="depart-btn">
                            <i class="ti-menu"></i>
                            <span>All departments</span>
                            <ul class="depart-hover" style="text-align: left;">
                                <li><a href="javascript:void(0)">Man - Kaos</a></li>
                                <li><a href="javascript:void(0)">Man - Hodie</a> </li>
                                <li><a href="javascript:void(0)">Man - Sepatu</a> </li>
                                <li><a href="javascript:void(0)">Man - Tas</a></li>
                                <li><a href="javascript:void(0)">Woman - Kaos</a> </li>
                                <li><a href="javascript:void(0)">Woman - Hodie</a></li>
                                <li><a href="javascript:void(0)">Woman - Sepatu</a></li>
                                <li><a href="javascript:void(0)">Woman - Tas</a> </li>
                                <li><a href="javascript:void(0)">Kid - Kaos</a></li>
                                <li><a href="javascript:void(0)">Kid - Hodie</a> </li>
                                <li><a href="javascript:void(0)">Kid - Sepatu</a> </li>
                                <li><a href="javascript:void(0)">Kid - Tas</a></li>
                            </ul>
                        </div>
                    </div>
                    <nav class="nav-menu mobile-menu">
                        <ul>
                            <li class="active"><a href="javascript:void(0)">Home</a></li>
                            <li><a href="javascript:void(0)">Shop</a></li>
                            <li><a href="#">Kategori</a>
                                <ul class="dropdown" style="text-align: left;">
                                    <li><a href="javascript:void(0)">Man</a></li>
                                    <li><a href="javascript:void(0)">Woman</a></li>
                                    <li><a href="javascript:void(0)">Kid</a></li>
                                    <li><a href="javascript:void(0)">Azel</a></li>
                                </ul>
                            </li>
                            <li><a href="javascript:void(0)">Blog</a></li>
                            <li><a href="javascript:void(0)">Contact</a></li>
                            <li><a href="javascript:void(0)">FAQ</a>
                            </li>
                        </ul>
                    </nav>
                    <div id="mobile-menu-wrap">
                        <div class="slicknav_menu">
                            <a href="#" aria-haspopup="true" role="button" tabindex="0"
                                class="slicknav_btn slicknav_collapsed" style="outline: currentcolor none medium;">
                                <span class="slicknav_menutxt">MENU</span>
                                <span class="slicknav_icon">
                                    <span class="slicknav_icon-bar"></span>
                                    <span class="slicknav_icon-bar"></span>
                                    <span class="slicknav_icon-bar"></span>
                                </span>
                            </a>
                            <nav class="slicknav_nav slicknav_hidden" style="display: none;" aria-hidden="true" role="menu">
                                <ul>
                                    <li class="active"><a href="javascript:void(0)" role="menuitem">Home</a></li>
                                    <li><a href="javascript:void(0)" role="menuitem">Shop</a></li>
                                    <li class="slicknav_collapsed slicknav_parent"><a href="#" role="menuitem" aria-haspopup="true" tabindex="-1" class="slicknav_item slicknav_row" style="outline: currentcolor none medium;"><a href="#">Kategori</a>
                                            <span class="slicknav_arrow">►</span></a>
                                        <ul class="dropdown slicknav_hidden" role="menu" style="display: none;"
                                            aria-hidden="true">
                                            <li><a href="javascript:void(0)" role="menuitem" tabindex="-1">Man</a></li>
                                            <li><a href="javascript:void(0)" role="menuitem" tabindex="-1">Woman</a></li>
                                            <li><a href="javascript:void(0)" role="menuitem" tabindex="-1">Kid</a></li>
                                            <li><a href="javascript:void(0)" role="menuitem" tabindex="-1">Azel</a></li>
                                        </ul>
                                    </li>
                                    <li><a href="javascript:void(0)" role="menuitem">Blog</a></li>
                                    <li><a href="javascript:void(0)" role="menuitem">Contact</a></li>
                                    <li><a href="javascript:void(0)" role="menuitem">FAQ</a>
                                    </li>
                                </ul>
                            </nav>
                        </div>
                    </div>
                </div>
            </div>
        </header>
        <!-- Header End -->
    </div>
</template>

<script>
import axios from "axios";
export default {
  name: "HeaderShayna",
  // props:['customer'],
  data() {

    return {
        customer: null,
        keranjangUser: [],
    };
  },
    async created()
    {
        const response = await axios.get('customer'); 
        
        // const response = await axios.get('customer',{
        //     headers: {
        //       Authorization: 'Bearer' + localStorage.getItem('token')
        //     }
        // });
        
        this.customer = response.data; 
    },
  methods: {
    handleClick(){
        // alert('a');
      localStorage.removeItem('token');
      // window.location.reload();
      this.$router.go()
      // this.$router.push('/login')
    },
    removeItem(idx) {
      // cari tau id dari si item yang akan dihapus
      let keranjangUserStorage = JSON.parse(
        localStorage.getItem("keranjangUser")
      );
      let itemKeranjangUserStorage = keranjangUserStorage.map(
        (itemKeranjangUserStorage) => itemKeranjangUserStorage.id
      );

      //cocokkan id item dengan id yg di storage
      let index = itemKeranjangUserStorage.findIndex((id) => id == idx);
      this.keranjangUser.splice(index, 1);

      const parsed = JSON.stringify(this.keranjangUser);
      localStorage.setItem("keranjangUser", parsed);

      window.location.reload();
      // this.keranjangUser.splice(index,1);
      // const parsed = JSON.stringify(this.keranjangUser);
      // localStorage.setItem('keranjangUser',parsed);
    },
  },
  mounted() {
    if (localStorage.getItem("keranjangUser")) {
      try {
        this.keranjangUser = JSON.parse(localStorage.getItem("keranjangUser"));
      } catch (e) {
        localStorage.removeItem("keranjangUser");
      }
    }
  },
  computed: {
    totalHarga() {
      return this.keranjangUser.reduce(function (items, data) {
        // alert(items);
        return items + data.price;
      }, 0);
    },
  },
};
</script>

<style scoped>
.photo-item {
  width: 80px;
  height: 80px;
}

.header-text a {
  color: #252525;
  padding-right: 10px;
}

.login-panel {  
  padding-right: 10px;
}
</style>