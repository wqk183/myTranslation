<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5>简单/便捷/易用</h5>
   <translateForm v-on:formSubmit="translateText"></translateForm>
   <translateOutput v-text="translatedText"></translateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'app',
  data(){
    return{
      translatedText:""
    }
  },
  components: {
    TranslateForm,TranslateOutput
  },
  methods:{
      translateText(text,language){
        //alert(text);
        this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20190624T033609Z.879dfee5391e4e2c.64c6b2ca15bf961de69b7c053199a60b0e82e0d9&lang='+language+'&text='+text)
          .then((response)=>{
           //console.log(response.body.text[0]);
            this.translatedText=response.body.text[0];
          })
      }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
