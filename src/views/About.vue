/* eslint-disable new-cap */
<template>
  <div>
   <v-container>
      <v-row justify="center">
      <v-col cols="4">
        <h2 style="font-family: Gilroy-Semibold">CONVERTER SVG to PDF</h2>
        <!-- <v-text-field v-model="fname" label="Name"></v-text-field> -->
        <v-btn @click="print" color="orange">Create</v-btn>
        <v-text-field v-model="itemLength.count"></v-text-field>
      </v-col>
      <v-col cols="auto" v-show="true">
        <htmSl :itemLength="itemLength" />
      </v-col>
    </v-row>
   </v-container>
  </div>
</template>

<script>
import htmSl from './htmls.vue'
export default {
  data () {
    return {
      itemLength: { count: 4 }
    }
  },
  components: { htmSl },
  computed: {

  },
  watch: {

  },
  methods: {
    print () {
      // eslint-disable-next-line no-undef
      printJS({
        printable: 'print_bill',
        css: ['@import url(\'https://fonts.googleapis.com/css2?family=Roboto+Mono:wght@100;400;600&display=swap\');'],
        font: 'Roboto Mono',
        type: 'html'
      })
    }
  }
}
</script>

<style>
</style>
