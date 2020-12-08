/* eslint-disable new-cap */
<template>
  <div>
   <v-container>
      <v-row justify="center">
      <v-col cols="4">
        <h2 style="font-family: Gilroy-Semibold">HELLO WORLd</h2>
        <v-text-field v-model="fname" label="Name"></v-text-field>
        <!-- <v-text-field v-model="course" label="Course Name"></v-text-field>
        <v-text-field v-model="type" label="type" hint="golden, bronze, silver"></v-text-field>
        <v-text-field v-model="created_at" label="created time"></v-text-field>
        <v-text-field v-model="image" label="image URL"></v-text-field> -->
        <v-btn @click="getSVG">Create</v-btn>
      </v-col>
      <v-col cols="8">
        <v-card v-html="svg"></v-card>
      </v-col>
    </v-row>
   </v-container>
  </div>
</template>

<script>
import { jsPDF } from 'jspdf'
import image from '@/assets/image.js'
import 'svg2pdf.js'

export default {
  data () {
    return {
      svg: image(),
      fname: '',
      course: '',
      type: '',
      created_at: new Date().getFullYear(),
      image: '',
      colors: [
        { top: '#FFCC00', middle: 'red', bottom: 'blue' },
        { top: 'green', middle: 'orange', bottom: 'blue' },
        { top: 'black', middle: 'green', bottom: 'blue' }
      ],
      color: {
        top: '#483d00',
        bottom: '#FFFCEB',
        middle: '#FFCC00'
      }
    }
  },
  computed: {
    // svg () {
    //   return image('hello')
    // }
  },
  watch: {
    type (value) {
      if (value.toLowerCase() === 'golden') this.color = this.colors[0]
      if (value.toLowerCase() === 'bronze') this.color = this.colors[1]
      if (value.toLowerCase() === 'silver') this.color = this.colors[2]
      if (value === '') {
        this.color = {
          top: '#483d00',
          bottom: '#FFFCEB',
          middle: '#FFCC00'
        }
      }
    },
    fname (val) {
      this.svg = image(val)
    }
  },
  methods: {
    getSVG () {
      // eslint-disable-next-line new-cap
      const doc = new jsPDF({ format: 'a4', orientation: 'l' })
      doc.addFont('Gilroy-Semibold.woff', 'NotoSansCJKjp1', 'normal')
      doc.setFont('NotoSansCJKjp1')
      const element = document.getElementById('svg_pdf')
      doc
        .svg(element, {
          x: -14,
          y: 0,
          width: 325,
          height: 210
        })
        .then(() => {
          // save the created pdf
          doc.save('myPDF.pdf')
        })
    }
  }
}
</script>

<style>
</style>
