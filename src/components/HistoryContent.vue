<template>
    <div>
        <div class="container-fluid">
            <div class="row">
                <div class="col-sm-1" id="side-menu">
                    <div id="left-content">
                        <div id="left-menu">
                            <div id="fork"><img src="../assets/img/fork.png"></div>
                            <div id="clipboard"><img src="../assets/img/clipboard.png"></div>
                            <div id="add"><img src="../assets/img/add.png"></div>
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

                <div class="col-md-11 center-content">
                    <div class="row">
                        <div class="col-md-3 my-3 box box-1">
                            <div class="circle">
                                <img src="../assets/img/red-circle.png">
                            </div>
                            <div class="box-content">
                                <p class="box-content-title">Today's Income</p>
                                <h3 class="box-content-value">Rp. 1.000.000</h3>
                                <p class="box-content-percent">+2% Yesterday</p>
                            </div>
                        </div>

                        <div class="col-md-3 my-3 box box-2">
                            <div class="circle">
                                <img src="../assets/img/blue-circle.png">
                            </div>
                            <div class="box-content">
                                <p class="box-content-title">Orders</p>
                                <h3 class="box-content-value">3.270</h3>
                                <p class="box-content-percent">+5% Last Week</p>
                            </div>
                        </div>

                        <div class="col-md-3 my-3 box box-3">
                            <div class="circle">
                                <img src="../assets/img/purple-circle.png">
                            </div>
                            <div class="box-content">
                                <p class="box-content-title">This Year's Income</p>
                                <h3 class="box-content-value">Rp. 100.000.000.000</h3>
                                <p class="box-content-percent">+10% Last Year</p>
                            </div>
                        </div>
                    </div>

                    <!-- <div class="col-md-11 charts">
                        <div class="ch-revenue">
                            <div class="revenue">Revenue</div>
                            <div class="month-wrapper">
                                <div class="month">
                                    <p>Month</p>
                                    <div class="drop-img">
                                    <img src="../assets/img/arrow.png">
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div> -->

                    <div class="col-md-11 order-table">
                        <div class="ch-order">
                            <div class="recent">Recent Order</div>
                            <div class="day-wrapper">
                            <div class="today">
                                <p>Today</p>
                                <div class="drop-img">
                                <img src="../assets/img/arrow.png">
                                </div>
                            </div>
                            </div>
                        </div>
                        <table class="table text-center">
                            <tr class="col-12">
                            <th>INVOICES</th>
                            <th>CASHIER</th>
                            <th>DATE</th>
                            <th>ORDERS</th>
                            <th>AMOUNT</th>
                            </tr>

                            <tr v-for="history in hist" :key="history.id">
                            <td>{{history.invoices}}</td>
                            <td>{{history.cashier}}</td>
                            <td>{{history.date}}</td>
                            <td>{{history.orders}}</td>
                            <td>Rp. {{history.amount}}</td>
                            </tr>
                        </table>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      hist: []
    }
  },
  methods: {
    getHistory () {
      axios.get('http://localhost:3001/api/v1/history/getAll')
        .then((response) => {
          this.hist = response.data.data
        })
        .catch((err) => {
          console.log(err)
        })
    }
  },
  mounted () {
    this.getHistory()
  }
}
</script>
