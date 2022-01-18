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
                        <!-- v-for="(card,index) in cards" -->
                        <Album 
                        v-for="(card,index) in getFilter" 
                        :key="index"
                        :card="card"
                        />
                  </div>
                <div class="text-white" v-else>
                    <h1>Loading</h1>
                    </div>
              </div>
          </div>
      </div>
  </main>
</template>


<script>
// import
import axios from 'axios';
import Album from './Album.vue';
import Select from './Select.vue';

export default {
    components: {
        Album,
        Select,
    },
    name:"Main",
    data() {
        return {
            textSearch: "all",
            cards:null,
            // vModel: ""
            // getGenre: null,
            queryApi: "https://flynn.boolean.careers/exercises/api/array/music"
        }
    },
    created() {
        this.getAxios()       
    },

    computed:{
        getFilter() {
            if (this.textSearch === "all") {
                return this.cards
            }else {
                 return this.cards.filter((element) => 
                 element.genre.toLowerCase() == this.textSearch.toLowerCase()
                )
            }       
        }
    },
    
    methods: {
        getAxios: function () {
            axios.get(this.queryApi)
            .then(res => {
                this.cards = res.data.response;
                // this.getGenre =  res.data.response;
            })
            .catch(err => {
                console.error(err); 
            })
        },


        searchGenre: function (text) {
            this.textSearch = text
        }

        // searchGenre: function (text) {
        //     this.cards = this.getGenre;
        //     if (this.vModel != "all") {
        //         this.cards = this.cards.filter((element) => {
        //             element.genre.toLowerCase().includes(this.vModel.toLowerCase())
        //         })
        //     }
        // },
        
    },
}
</script>

<style lang="scss" scoped>
    .bc-main {
        background-color: #1e2d3b;
        height: 94vh;      
    }     
</style>