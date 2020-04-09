<template>
   
      <v-layout row wrap  align-end>
      <v-flex xs3 offset-xs9 align-end>
         <v-col cols="12" sm="4">
  <v-btn class="ma-3 primary" @click="changeColor">Color Violet</v-btn>
  <v-btn class="ma-3 primary" @click="changeFontSize">Font Size 51</v-btn>
  <v-btn class="ma-3 primary" @click="changeBackground">Background Yellow</v-btn>
       </v-col>
      </v-flex>
      </v-layout>
    
</template>

<script>
  export default {
    name: 'ButtonsComponent',
    props:['selectText'],
    data(){
      return{
       
      }
    },
    mounted(){
    },
    methods:{
      changeFontSize(){
         this.$emit('changeFont','fontSize',false,'51px')
        console.log(this.selectText)
      },
      changeColor(){
        this.$emit('changeCol', 'foreColor',false,'violet')
        console.log(this.selectText)
      },
      changeBackground(){
        this.$emit('changeBg','backColor',false,'yellow')
         console.log(this.selectText)
      }
    }
  }
</script>
<style>
.btn{
  top: 200px
}
</style>
