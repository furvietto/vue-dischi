.<template>
    <div class="row h-350">
        <div class="col pb-2 pt-2 card text-center bc-card">
                <img :src="card.poster" alt="">
                <h1 class="mb-3 mt-3 text-white">{{card.title}}</h1>
                <h2 class="fs-6"> {{card.author}}</h2>
                <h3 class="fs-6"> {{card.year}}</h3>
        </div>
    </div>
</template>

<script>
export default {
    name: "Album",
    props : ["card"]
}
</script>

<style lang="scss" scoped>
     .h-350 {
         height: 350px;
            .bc-card {
            background-color: #2e3a46;
            color: #797e7a ;
                h1 {
                    text-transform: uppercase;
                    font-size: 1.2em;
                }
        }
     }
</style>