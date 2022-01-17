.<template>
  <div class="container-fluid">
      <div class="row p-2">
          <div class="col-12">
              <img src="../assets/img/logo-small.svg" alt="">
          </div>
      </div>
  </div>
</template>

<script>
export default {
    name:"Header"
}
</script>

<style lang="scss" scoped>
.container-fluid {
    background-color: #2e3a46;
    img {
        width: 30px;
        filter: invert(10);
    }
}
    
</style>