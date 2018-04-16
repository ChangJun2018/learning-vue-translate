<template>
  <div id="translatefrom" class="row">
    <div class="col-md-6 col-md-offset-3">
      <form class="well from-inline" v-on:submit="formSubmit">
        <input type="text" class="form-control cjmargin" placeholder="输入需要翻译的内容" v-model="textToTranslate">
        <select v-model="language" class="form-control cjmargin">
          <option value="en">English</option>
          <option value="ru">Russian</option>
          <option value="ko">Korean</option>
          <option value="ja">Japanese</option>
        </select>
        <input type="submit" class="btn btn-primary btn-lg cjmargin" value="翻译"/>
      </form>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'translatefrom',
    data: function () {
      return {
        textToTranslate: "",
        language: ""
      }
    },
    methods: {
      formSubmit: function (e) {
        this.$emit("fromSubmit", this.textToTranslate, this.language);
        e.preventDefault();
      }
    },
    created:function(){
      this.language="en";
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#translatefrom{
  border: 1px #ffff solid ;
}
.cjmargin{
    margin-top: 20px;
  }
</style>
