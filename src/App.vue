<template>
  <div class="text-center" id="app">
    <h1>Word Translator</h1>
    <h5>Powered by Vue.js & Yandex</h5>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm></TranslateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'
export default {
  name: 'App',
  components:{
    TranslateForm,
    TranslateOutput
  },
  data: function(){
    return {
      translatedText:''
    }
  },
  methods: {
    translateText:function(text, language){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20181129T201637Z.8b0b461ed7b9a2f5.4ced545644f3a68478ce91c83b84c33f9e86adcd&lang='+language+'&text='+text).then((response) => {
        this.translatedText = response.body.text[0];
      });
    }
  }
}
</script>

<style>
body {
  background:#fefefe;
}
</style>
