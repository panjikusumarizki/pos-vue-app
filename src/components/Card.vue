<template>
    <div>
        <div id="food-content">
            <img fluid :src="`http://localhost:3001/${products.picture}`" id="img-card">
            <p class="name">{{products.name}}</p>
            <h4 class="price">Rp. {{products.price}}</h4>
            <div class="d-flex mb-3" id="bt-card">
                <b-button variant="primary" v-b-modal.my-modals>
                    <b-icon icon="pencil-square"></b-icon>
                </b-button>

                <b-button variant="success">
                    <b-icon icon="cart4"></b-icon>
                </b-button>

                <b-button @click="onGet()" variant="danger">
                    <b-icon icon="x"></b-icon>
                </b-button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  props: ['products'],
  methods: {
    onGet () {
      this.$emit('emitId')
    }
  }
}
</script>

<style scoped>
#bt-card {
    justify-content: space-evenly;
}
</style>
