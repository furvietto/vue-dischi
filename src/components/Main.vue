.<template>
  <main class="bc-main">
      <div class="container-fluid pb-5 pt-5">
          <div class="row d-flex justify-content-center">
              <div class="col-8" >
                  <div v-if="cards" class="row justify-content-around row-cols-5">
                        <Album 
                        class="p-4 col"
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
import Album from './Album.vue'

export default {
    components: {
        Album,
    },
    name:"Main",
    data() {
        return {
            cards:null,
            queryApi: "https://flynn.boolean.careers/exercises/api/array/music"
        }
    },
    created() {
        setTimeout(() => {
            this.getAxios()
        }, 2000);
        
    },

    methods: {
        getAxios: function () {
            axios.get(this.queryApi)
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
    }
     
     
</style>