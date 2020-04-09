<template>
  <v-app>
  <v-row>
  <v-col cols="12" md="6"> 
   <v-textarea 
      outlined
      class="mx-5"
      label="Edit text"
      v-model="text"
      @click="getSelectionText"
    >
   </v-textarea>
  <v-btn class="ma-3 primary" @click="add">add and save text</v-btn>
 
  </v-col>
  <v-col cols="12" md="6"> 
   <v-card > 
   <div  class="myeditor relative-position cursor_normal none_outline"
     style="color: rgb(255, 255, 255); opacity: 1; border-radius: 6px; transform: rotate(0deg); border: 0px solid rgb(70, 144, 247); padding: 10px; text-align: center; letter-spacing: 0px; font-size: 32px; font-family: Aleo; font-weight: 300; text-decoration: none; box-shadow: rgb(0, 0, 0) 0px 0px 0px 0px; text-transform: initial; font-style: normal; z-index: 2002; text-shadow: rgba(0, 0, 0, 0.2) 2px 2px 0px; line-height: 1.5em;"
     spellcheck="false"
     @click="getSelectionText"
     :contenteditable="contenteditable"
     >
        {{editedText}}
  <!-- <span style="background-color: rgb(248, 187, 208); padding-left:3px; padding-right: 3px; border-radius: 4px;">{{text}}</span>
    <br/>
    <span style="background-color: rgb(248, 187, 208); padding-left:3px; padding-right: 3px; border-radius: 4px;">My lovely</span>
    <span 
    style="color: rgb(136, 14, 79); font-size: 54px">little</span>
  <span style="color: rgb(186, 104, 200); background-color: rgb(248, 187, 0);">Ponny</span>
  -->
   </div>
  </v-card>
  </v-col>
  </v-row>
  <app-buttons 
  :selectText="selectText" 
  @changeCol="change"
  @changeFont="change"
  @changeBg="change"
  ></app-buttons>
  </v-app>
</template>

<script>

import ButtonsComponent from './components/ButtonsComponent.vue'
export default {
  name: 'App',

  components: {
   'app-buttons': ButtonsComponent,
  },
  data(){
   return {
     text: "Hi My lovely Ponny",
     selectText:'',
     newText:'',
     contenteditable: false
     
   }
  },
  computed:{
    editedText(){
      if(this.newText == '') return this.text
      return this.newText
    }
  },
  methods: {
    getSelectionText(){
      var text = ''
      if (window.getSelection) {
        text = window.getSelection().toString();
    } else if (document.selection && document.selection.type != "Control") {
        text = document.selection.createRange().text;
    }
      console.log( text)
      this.selectText = text;
      this.contenteditable = true
        return text;
    },
    add(){
      this.newText = this.text
      // this.text =''
    },
    // changeFontSize(){
    //   if(this.selectText !== ''){
    //     this.styleFontSelected()
    //   } 
    // },
    // changeBackGround(){
    //    if(this.selectText !== ''){
    //      this.styleSelected()  
    //   } 
    // },
    // styleSelected() {
    //    var bg = document.createElement("span");
    //     bg.style.backgroundColor = "yellow";
    //     window.getSelection().getRangeAt(0).surroundContents(bg);
    // },
    // styleColorSelected() {
    //    var col = document.createElement("span");
    //     col.style.color = "violet";
    //     window.getSelection().getRangeAt(0).surroundContents(col);
    // },
    // styleFontSelected() {
    //    var font = document.createElement("span");
    //     font.style.fontSize = "51"+"px";
    //     window.getSelection().getRangeAt(0).surroundContents(font);
    // },
    change (style, ui, value) {
      var inui = false;
      var ivalue = null;
      if (arguments[1]) {
        inui = ui;
      }
      if (arguments[2]) {
        ivalue = value;
      }
      document.execCommand(style, inui, ivalue);
    }
  },
  mounted(){
   
  }
   
};
</script>
<style>
.active{
  color:violet;
}
.font{
  font-size: 51px;
}
.bg_text{
  background-color: rgb(240, 243, 40);
}
.myeditor {
  padding: 5px;
  margin: 5px;
  min-height: 150px;
  text-align: center;
}
</style>
