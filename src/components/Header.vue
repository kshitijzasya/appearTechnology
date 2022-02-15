<template>
    <div class="row no_margin custom_postion">
      <div class="col-md-3 no_margin">
        <div class="bg_left vh-100"></div>
      </div>

      <div class="col-md-9 no_margin">
        <div class="bg_right vh-100">
          <img class="vh-100" src="../assets/loan-calc.png" />
        </div>
      </div>
    </div>
</template>

<script>
export default {
    name: 'Header',    
}
</script>
<style scoped>
.custom_postion {
  position:fixed;
  width:100%;
}
</style>
