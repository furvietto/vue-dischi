.<template>
  <select v-model="selectedGenre" @change="$emit('doSearch', selectedGenre)" name="search" id="search">
    <option value="all">All</option>
    <option value="rock">Rock</option>
    <option value="jazz">Jazz</option>
    <option value="metal">Metal</option>
    <option value="pop">Pop</option>
</select>
</template>

<script>
export default {
    name:"Select",
    data() {
        return {
            selectedGenre: "all",
        }
    },
}
</script>

<style>
</style>