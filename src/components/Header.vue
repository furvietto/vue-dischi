.<template>
  <div class="container-fluid">
      <div class="row p-3 bg-light">
          <div class="col-12 d-flex justify-content-end">
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
    img {
        width: 30px;
        filter: invert(10);
    }
</style>