.<template>
  <main class="bc-main">
      <div class="container-fluid">
          <div class="row ">
              <div class="col pb-2 d-flex justify-content-end">
                  <Select 
                  @doSearch="searchGenre($event)"
                  />
              </div>
          </div>
          <div class="row justify-content-center">
              <div class="col-8" >
                  <div v-if="cards" class="row gap-3 justify-content-around row-cols-6">
                        <Album 
                        v-for="(card,index) in cards"
                        :key="index"
                        :card="card"
                        />
                  </div>
                <div class="text-white" v-else>LOADING...</div>
              </div>
          </div>
      </div>
  </main>
</template>

<script>
import axios from 'axios';
import Album from './Album.vue';
import Select from './Select.vue'

export default {
    components: {
        Album,
        Select,
    },
    name:"Main",
    data() {
        return {
            getGenre: null,
            cards:null,
            queryApi: "https://flynn.boolean.careers/exercises/api/array/music"
        }
    },
    created() {
            this.getAxios()        
    },

    methods: {
        getAxios: function () {
            axios.get(this.queryApi)
            .then(res => {
                this.cards = res.data.response;
                this.getGenre = res.data.response;
            })
            .catch(err => {
                console.error(err); 
            })
        },

        searchGenre: function (text) {
        this.cards = this.getGenre
        if (text != "all") {
            let getArray = this.cards.filter(element => {
             if (element.genre.toLowerCase().includes(text.toLowerCase())) {
                 return true
             }
         })
         this.cards = getArray
        }
        }
        
    },
}
</script>

<style lang="scss" scoped>
    .bc-main {
        background-color: #1e2d3b;
        height: 94vh;      
    }
     
     
</style>