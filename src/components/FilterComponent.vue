<template>
  <div id="filterComponent" class="filter">
    <a href="javascript:void(0)" class="closebtn" @click="closeFilter()">&times;</a>
    <div class="filter-content">
      <h2><strong>Filter</strong></h2>
      <div class="row">
        <div class="col">
          <span class="btn btn-outline-primary">Primary <i class="bi bi-x-circle-fill"></i></span>
        </div>
      </div>
      <div class="row">
        <div class="col">
          <span class="btn btn-outline-primary">Primary <i class="bi bi-x-circle-fill"></i></span>
        </div>
      </div>
      <div class="row">
        <div class="col">
          <span class="btn btn-outline-primary">Clear All Filter</span>
        </div>
      </div>
      <div class="input-group">
        <label for="customRange1" class="form-label"><strong>Point Needed</strong></label>
        <input type="range" class="form-range" min="10000" max="500000" id="customRange1">
      </div>
      <div>
        <label for="checkbox" class="form-label"><strong>Award Type</strong></label>
        <div class="form-check">
          <input class="form-check-input" type="checkbox" value="" id="flexCheckChecked" checked>
          <label class="form-check-label" for="flexCheckChecked">
            All Type
          </label>
        </div>
        <div class="form-check">
          <input class="form-check-input" type="checkbox" value="" id="flexCheckChecked" checked>
          <label class="form-check-label" for="flexCheckChecked">
            Vouchers
          </label>
        </div>
        <div class="form-check">
          <input class="form-check-input" type="checkbox" value="" id="flexCheckChecked" checked>
          <label class="form-check-label" for="flexCheckChecked">
            Products
          </label>
        </div>
        <div class="form-check">
          <input class="form-check-input" type="checkbox" value="" id="flexCheckChecked" checked>
          <label class="form-check-label" for="flexCheckChecked">
            Giftcards
          </label>
        </div>
      </div>
      <div class="d-grid gap-2">
        <input type="button" class="btn btn-primary btn-lg" value="Filter">
      </div>
    </div>
  </div>
</template>

<script>
export default {
    data() {
    return {
      
    }
  },
  methods: {
    closeFilter(){
      document.getElementById("filterComponent").style.width = "0px";
    }
  }
}
</script>

<style scoped>
#filterComponent {
    background-color: rgb(255, 255, 255);
    width: 0;
    height: 100%;
    position: fixed;
    z-index: 1031;
    top: 0;
    left: 0;
    overflow-x: hidden;
    padding-top: 60px; /* Place content 60px from the top */
}

.filter a {
  padding: 8px 8px 8px 32px;
  text-decoration: none;
  font-size: 25px;
  color: #818181;
  display: block;
}

.filter .filter-content {
  padding: 8px 8px 8px 32px;
}

.filter .closebtn {
  position: absolute;
  top: 0;
  right: 25px;
  font-size: 36px;
  margin-left: 50px;
}
</style>