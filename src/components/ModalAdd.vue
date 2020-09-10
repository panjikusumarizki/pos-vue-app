<template>
    <div>
        <b-modal id="my-modal" hide-header hide-footer>
          <h4>Add Item</h4>

                <form class="form first-form" @submit="uploadData" enctype="multipart/form-data">
                  <div class="form-group row">
                    <label for="inputName" class="col-sm-2 col-form-label">Name</label>
                    <div class="col-sm-10">
                      <input type="text" class="form-control input-fom" id="inputName" v-model="name">
                    </div>
                  </div>

                  <div class="form-group row">
                    <label class="col-sm-2 col-form-label">Image</label>
                    <div class="col-sm-10">
                      <b-form-file placeholder="Choose image" class="input-fom" @change="onProcessFile($event)"></b-form-file>
                    </div>
                  </div>

                  <div class="form-group row">
                    <label for="inputPrice" class="col-sm-2 col-form-label">Price</label>
                    <div class="col-sm-7">
                      <input type="text" class="form-control input-fom" id="inputPrice" v-model="price">
                    </div>
                  </div>

                  <div class="form-group row">
                    <label for="category" class="col-sm-2 col-form-label">Category</label>
                    <select class="form-control col-sm-5 ml-3 input-fom" v-model="id_category">
                      <option selected :value="null">Category</option>
                      <option v-for="(item, index) in ctg" :key="index" :value="item.id">{{item.category_name}}</option>
                    </select>
                  </div>

                  <div class="two-button">
                    <div>
                      <input type="button" value="Cancel" class="btn btn-cancel-add">
                    </div>

                    <div>
                      <input type="submit" value="Add" class="btn btn-add">
                    </div>
                  </div>
                </form>
        </b-modal>
    </div>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      ctg: null,
      name: null,
      image: null,
      price: null,
      id_category: null
    }
  },
  methods: {
    onProcessFile (event) {
      this.image = event.target.files[0]
    },
    uploadData () {
      const formData = new FormData()
      formData.append('name', this.name)
      formData.append('picture', this.image)
      formData.append('price', this.price)
      formData.append('id_category', this.id_category)

      axios.post('http://localhost:3001/api/v1/product/insert', formData)
        .then((response) => {
          console.log(response)
          alert('Success insert data')
        })
        .catch((err) => {
          console.log(err)
        })
    },
    getCategory () {
      axios.get('http://localhost:3001/api/v1/category/getAll')
        .then((response) => {
          this.ctg = response.data.data
        })
        .catch((err) => {
          console.log(err)
        })
    }
  },
  mounted () {
    this.getCategory()
  }
}
</script>
