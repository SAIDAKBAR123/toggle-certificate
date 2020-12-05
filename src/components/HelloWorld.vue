/* eslint-disable new-cap */
<template>
  <div>
   <v-container>
      <v-row justify="center">
      <v-col cols="6">
        <v-text-field v-model="fname" label="Name"></v-text-field>
        <v-text-field v-model="course" label="Course Name"></v-text-field>
        <v-text-field v-model="type" label="type" hint="golden, bronze, silver"></v-text-field>
        <v-text-field v-model="created_at" label="created time"></v-text-field>
        <v-text-field v-model="image" label="image URL"></v-text-field>
        <v-btn @click="getSVG">Create</v-btn>
      </v-col>
      <v-col cols="6">
        <svg
          id="svg_pdf"
          xmlns="http://www.w3.org/2000/svg"
          xmlns:xlink="http://www.w3.org/1999/xlink"
          width="842"
          height="595"
          viewBox="0 0 842 595"
        >
          <defs>
            <clipPath id="clip-Custom_Size_1">
              <rect width="842" height="595" />
            </clipPath>
          </defs>
          <g
            id="Custom_Size_1"
            data-name="Custom Size – 1"
            clip-path="url(#clip-Custom_Size_1)"
          >
            <rect width="842" height="595" fill="#fff" />
            <rect
              id="Rectangle_3"
              data-name="Rectangle 3"
              width="842"
              height="364"
              transform="translate(0 115)"
              :fill="color.middle"
              opacity="0.08"
            />
            <rect
              id="Rectangle_1"
              data-name="Rectangle 1"
              width="842"
              height="116"
              transform="translate(0 479)"
              :fill="color.bottom"
            />
            <rect
              id="Rectangle_2"
              data-name="Rectangle 2"
              width="842"
              height="116"
              :fill="color.top"
            />
            <text
              id="CERTIFICATE"
              transform="translate(250 84)"
              fill="rgba(255,255,255,0.35)"
              font-size="62"
              font-family="YuGothicUI-Regular, Yu Gothic UI"
            >
              <tspan x="0" y="0">CERTIFICATE</tspan>
            </text>
            <text
              id="Name:_"
              data-name="Name: "
              transform="translate(186 155)"
              fill="#707070"
              font-size="20"
              font-family="YuGothicUI-Regular, Yu Gothic UI"
            >
              <tspan x="0" y="22">Name:</tspan>
            </text>
            <text
              id="Saidakbar_Makhmudkhujaev"
              data-name="Saidakbar Makhmudkhujaev"
              transform="translate(264 155)"
              fill="#707070"
              font-size="20"
              font-family="YuGothicUI-Regular, Yu Gothic UI"
            >
              <tspan x="0" y="22">{{ fname }}</tspan>
            </text>
            <text
              id="Intro_to_IT"
              data-name="Intro to IT"
              transform="translate(264 217)"
              fill="#707070"
              font-size="20"
              font-family="YuGothicUI-Regular, Yu Gothic UI"
            >
              <tspan x="0" y="22">{{ course }}</tspan>
            </text>
            <text
              id="Golden"
              transform="translate(264 279)"
              fill="#707070"
              font-size="20"
              font-family="YuGothicUI-Regular, Yu Gothic UI"
            >
              <tspan x="0" y="22">{{ type }}</tspan>
            </text>
            <text
              id="_2020_20_20"
              data-name="2020/20/20"
              transform="translate(264 335)"
              fill="#707070"
              font-size="20"
              font-family="YuGothicUI-Regular, Yu Gothic UI"
            >
              <tspan x="0" y="22">{{ created_at }}</tspan>
            </text>
            <text
              id="Course_Name:_"
              data-name="Course Name: "
              transform="translate(123 217)"
              fill="#707070"
              font-size="20"
              font-family="YuGothicUI-Regular, Yu Gothic UI"
            >
              <tspan x="0" y="22">Course Name:</tspan>
            </text>
            <text
              id="TYPE:"
              transform="translate(199 279)"
              fill="#707070"
              font-size="20"
              font-family="YuGothicUI-Regular, Yu Gothic UI"
            >
              <tspan x="0" y="22">TYPE:</tspan>
            </text>
            <text
              id="Given:"
              transform="translate(186 335)"
              fill="#707070"
              font-size="20"
              font-family="YuGothicUI-Regular, Yu Gothic UI"
            >
              <tspan x="0" y="22">Given:</tspan>
            </text>
            <image id="Image_3" data-name="Image 3" width="202" height="260" transform="translate(559 165)" :xlink:href="image" />
          </g>
        </svg>
      </v-col>
    </v-row>
   </v-container>
  </div>
</template>

<script>
import { jsPDF } from 'jspdf'
import 'svg2pdf.js'

export default {
  data () {
    return {
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
    }
  },
  methods: {
    getSVG () {
      // eslint-disable-next-line new-cap
      const doc = new jsPDF({ format: 'a4', orientation: 'l' })

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
