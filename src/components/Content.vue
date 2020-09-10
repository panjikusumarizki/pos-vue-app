<template>
    <div>
        <div class="container-fluid">
            <div class="row">
                <div class="col-sm-1" id="side-menu">
                    <div id="left-content">
                        <div id="left-menu">
                            <div id="fork"><img src="../assets/img/fork.png"></div>
                            <router-link to="/history"><div id="clipboard"><img src="../assets/img/clipboard.png"></div></router-link>
                            <div id="add" v-b-modal.my-modal><img src="../assets/img/add.png"></div>
                        </div>
                    </div>

                    <div id="bottom-menu">
                        <div id="bottom-menu-content">
                            <div id="fork-bottom"><img src="../assets/img/fork.png"></div>
                            <div id="clipboard-bottom"><img src="../assets/img/clipboard.png"></div>
                            <div id="add-bottom"><img src="../assets/img/add.png"></div>
                        </div>
                    </div>
                </div>

                <div class="col-md-7 production" id="center-content">
                    <div>
                      <div class="row" id="sorting">
                        <input type="text" class="mb-4" placeholder="Product name..." v-model="find" @keyup="searchKey">
                        <div>
                          <b-dropdown id="dropdown-right" variant="outline-secondary" right text="Sort by" class="btn-ctg">
                            <b-dropdown-item v-model="sort" @click="sortByName">Sort by Product Name</b-dropdown-item>
                            <b-dropdown-item v-model="sort" @click="sortByCategory">Sort by Category</b-dropdown-item>
                            <b-dropdown-item v-model="sort" @click="sortByNew">Sort by Newest</b-dropdown-item>
                            <b-dropdown-item v-model="sort" @click="sortByPriceLow">Sort by Lowest Price</b-dropdown-item>
                            <b-dropdown-item v-model="sort" @click="sortByPriceHigh">Sort by Highest Price</b-dropdown-item>
                          </b-dropdown>
                        </div>
                      </div>
                      <div class="row">
                        <div class="col-6 col-sm-4 col-md-4 col-lg-4 food-card" v-for="(item, index) in product" :key="index">
                            <Card v-on:emitId="deleteProduct(item.id)" :products="item"/>
                        </div>
                      </div>
                    </div>
                </div>

                <div class="col-md-4 right-content">
                    <div id="cart-list">
                        <div>
                            <img src="../assets/img/empty.png">
                        </div>
                        <div><h5>Your cart is empty</h5></div>
                        <div><p>Please add some item from the menu</p></div>
                    </div>

                    <div class="cart-list-select">
                        <div class="cart-select">
                            <img src="../assets/img/cappucino.png" class="img-fluid">
                                <div class="side">
                                    <h4>Salmon truffle teriyaki teriyaki</h4>
                                    <div class="btn-qty">
                                        <div class="button"><p>-</p></div>
                                        <div class="button number">1</div>
                                        <div class="button">+</div>
                                    </div>
                                </div>
                            <div class="price-item text-right">Rp. 15.000</div>
                        </div>

                        <table class="total">
                            <tr>
                                <th width="60%" class="total-title">Total :</th>
                                <td class="price-total text-right">Rp. 105.000</td>
                            </tr>
                        </table>

                        <div class="tax">*Belum termasuk ppn</div>

                        <div>
                            <button class="btn btn-block btn-checkout py-3">Checkout</button>
                        </div>

                        <div>
                            <button class="btn btn-block btn-cancel mt-3 py-3 mb-2">Cancel</button>
                        </div>
                    </div>
                </div>
            </div>
            <Modal/>
            <!-- <Modaledit v-on:getEmit="getIds(item.id)"/> -->
        </div>
    </div>
</template>

<script>
import Card from '../components/Card'
import axios from 'axios'
import Modal from '../components/ModalAdd'
// import Modaledit from '../components/ModalEdit'

export default {
  name: 'content',
  data () {
    return {
      product: [],
      find: '',
      sort: ''
    }
  },
  components: {
    Card,
    Modal
    // Modaledit
  },
  methods: {
    getProduct () {
      axios.get('http://localhost:3001/api/v1/product/getAll')
        .then((response) => {
          this.product = response.data.data
        })
        .catch((err) => {
          console.log(err)
        })
    },
    searchKey () {
      axios.get(`http://localhost:3001/api/v1/product/getAll?name=${this.find}`)
        .then((response) => {
          this.product = response.data.data
        })
        .catch((err) => {
          console.log(err)
        })
    },
    sortByName () {
      axios.get('http://localhost:3001/api/v1/product/getAll?sortBy=name')
        .then((response) => {
          this.product = response.data.data
        })
        .catch((err) => {
          console.log(err)
        })
    },
    sortByCategory () {
      axios.get('http://localhost:3001/api/v1/product/getAll?sortBy=category_name')
        .then((response) => {
          this.product = response.data.data
        })
        .catch((err) => {
          console.log(err)
        })
    },
    sortByPriceLow () {
      axios.get('http://localhost:3001/api/v1/product/getAll?sortBy=price')
        .then((response) => {
          this.product = response.data.data
        })
        .catch((err) => {
          console.log(err)
        })
    },
    sortByPriceHigh () {
      axios.get('http://localhost:3001/api/v1/product/getAll?sortBy=price&sortType=desc')
        .then((response) => {
          this.product = response.data.data
        })
        .catch((err) => {
          console.log(err)
        })
    },
    sortByNew () {
      axios.get('http://localhost:3001/api/v1/product/getAll?sortBy=date_added&sortType=desc')
        .then((response) => {
          this.product = response.data.data
        })
        .catch((err) => {
          console.log(err)
        })
    },
    deleteProduct (id) {
      axios.delete(`http://localhost:3001/api/v1/product/delete/${id}`)
        .then((response) => {
          this.product = response.data.data
          this.getProduct()
        })
        .catch((err) => {
          console.log(err)
        })
    }
  },
  mounted () {
    this.getProduct()
  }
}
</script>
