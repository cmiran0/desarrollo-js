<template>

  <v-container>
    <v-row>
      <v-col>
        <span v-for="(item, index) in items" :key="index">
           <v-chip class="ma-2" v-if="item.BlockType==='LINE'">
             {{ item.Text }}
           </v-chip>
        </span>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "index",
  mounted() {
    this.$axios.get('/textract/1')
      .then(response => (
        this.word(response.data)
      ))

  },
  data() {
    return {
      items: null
    }
  },
  methods: {
    word(items) {
      let blocks = items["res"]["start"]["Blocks"]
      this.items = blocks
    }
  }
}
</script>

<style scoped>

</style>
