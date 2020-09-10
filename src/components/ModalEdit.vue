<template>
    <div>
        <b-modal id="my-modals" hide-header hide-footer>
            <h4>Edit item</h4>

            <form class="form first-form" enctype="multipart/form-data">
                <div class="form-group row">
                    <label for="inputName" class="col-sm-2 col-form-label">Name</label>
                    <div class="col-sm-10">
                      <input type="text" class="form-control input-fom" id="inputName">
                    </div>
                </div>

                <div class="form-group row">
                    <label class="col-sm-2 col-form-label">Image</label>
                    <div class="col-sm-10">
                      <b-form-file placeholder="Choose image" class="input-fom"></b-form-file>
                    </div>
                </div>

                <div class="form-group row">
                    <label for="inputPrice" class="col-sm-2 col-form-label">Price</label>
                    <div class="col-sm-7">
                      <input type="text" class="form-control input-fom" id="inputPrice">
                    </div>
                </div>

                <div class="form-group row">
                    <label for="category" class="col-sm-2 col-form-label">Category</label>
                    <select class="form-control col-sm-5 ml-3 input-fom">
                      <option selected>Category</option>
                    </select>
                </div>

                <div class="two-button">
                    <div>
                      <input type="button" value="Cancel" class="btn btn-cancel-add">
                    </div>

                    <div>
                      <input type="submit" value="Update" class="btn btn-add">
                    </div>
                  </div>
                </form>
        </b-modal>
    </div>
</template>
