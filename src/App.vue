<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5 class="text-muted">简单/易用/便捷</h5>
    <translatefrom v-on:fromSubmit="translateText"></translatefrom>
    <translateoutput v-text="translatedText" style="font-size: 32px"></translateoutput>
  </div>
</template>

<script>


  import Translatefrom from "./components/TranslateFrom";
  import Translateoutput from "./components/TranslateOutput";

  export default {
    components: {
      Translateoutput,
      Translatefrom
    },
    name: 'App',
    data: function () {
      return {
        translatedText: ""
      }
    },
    methods: {
      translateText: function (text, language) {
        this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180414T073133Z.b46e4a8d0de9a4b5.9896c3ffeb61ff013cc0488a525ece5b6bff296c&lang=' + language + '&text=' + text)
          .then((response) => {
            this.translatedText = response.body.text[0];
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
