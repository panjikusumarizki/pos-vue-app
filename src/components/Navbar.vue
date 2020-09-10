<template>
    <div>
        <div class="container-fluid">
            <b-navbar class="row navbar-expand-lg navbar-light bg-light" id="navbar">
                <div class="menu">
                    <img src="../assets/img/menu.png">
                </div>

                <div class="mx-auto" id="title">
                    <h4>Food Items</h4>
                </div>

                <div id="search-group">
                    <div id="search" @click="setDisplay()">
                        <img src="../assets/img/search.png">
                    </div>

                    <!-- <div id="search-box">
                        <input type="text" v-model="find" :class="searchDisplay" class="form-control" id="search-bar" placeholder="Product name..." @keyup="searchKey">
                    </div> -->
                </div>

                <div id="cart">
                    <h4>Cart</h4>
                    <span id="ellips">
                        <h5>0</h5>
                    </span>
                </div>

                <div id="ic-cart">
                    <img src="../assets/img/cart.png">
                    <span id="cart-span"><p>0</p></span>
                </div>
            </b-navbar>

            <!-- <div id="search-resp">
                <div id="img-search">
                    <img src="../assets/img/search-res.png">
                </div>
                <input type="text" v-model="find" class="form-control mt-2" id="search-res" placeholder="Product name...">
            </div> -->
        </div>
    </div>
</template>

<script>

// export default {
//   data () {
//     return {
//       searchDisplay: 'hide',
//       searching: false,
//       find: ''
//     }
//   },
//   methods: {
//     setDisplay () {
//       this.searching = !this.searching
//       if (!this.searching === true) {
//         this.searchDisplay = 'hide'
//       } else {
//         this.searchDisplay = 'show'
//       }
//     }
//   }
// }
</script>

<!-- <style scoped>
    .show {
        display: block;
    }
    .hide {
        display: none;
    }
</style> -->
