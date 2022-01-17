.<template>
  <main class="bc-main">
      <div class="container-fluid pb-5 pt-5">
          <div class="row d-flex justify-content-center">
              <div class="col-8" >
                  <div class="row row-cols-5">
                      <div 
                      class="p-4 col"
                      v-for="(card,index) in cards"
                      :key="index"
                      >
                      <div id="bc-card" class="row">
                          <div class="col pb-2 pt-2 card text-center">
                                <img :src="card.poster" alt="">
                                <h1>{{card.title}}</h1>
                                <h2> {{card.author}}</h2>
                                <h3> {{card.year}}</h3>
                               
                          </div>
                      </div>


                      </div>

                  </div>
                
              </div>
          </div>
      </div>
  </main>
</template>

<script>
import axios from 'axios';

export default {
    name:"Main",
    data() {
        return {
            cards:[],

        }
    },
    created() {
        this.getAxios()
    },

    methods: {
        getAxios: function () {
            axios.get("https://flynn.boolean.careers/exercises/api/array/music")
            .then(res => {
                this.cards = res.data.response;
            })
            .catch(err => {
                console.error(err); 
            })
        }
    },
}
</script>

<style lang="scss" scoped>
    .bc-main {
        background-color: #1e2d3b;
       #bc-card {
            background-color: #2e3a46;
        }
    }
     
</style>