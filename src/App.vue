<template>
  <div class="text-center" id="app">
    <h1>Awesome Translator </h1>

    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'
//import TranslateOutput from './components/TranslateWord'

export default {
  name: 'app',
  components: {
    TranslateForm,
    TranslateOutput
  },
  data: function(){
    return{
      translatedText:''
    }
  },
  methods: {
      translateText: function(text, language){
        this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170826T213257Z.36bdcf8d87f938f7.fe6d868a8d934ee68c724e7e22566a25eb63cae0&lang='+language+'&text=' + text)
        .then((response) => {
          this.translatedText = response.body.text[0];
        });
    }
  }
}
</script>

<style>
body {
background: #fefefe;
}
</style>
