.<template>
<header>
    <div class="container-fluid">
      <div class="row p-2">
          <div class="col-12">
              <img src="../assets/img/logo-small.svg" alt="">
          </div>
      </div>
  </div>
</header>
  
</template>

<script>
export default {
    name:"Header"
}
</script>

<style lang="scss" scoped>
.container-fluid {
    background-color: #2e3a46;
    height: 6vh;
    img {
        width: 30px;
    }
}
    
</style>