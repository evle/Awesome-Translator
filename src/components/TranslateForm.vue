<template>
  <div class="row" id="translateForm">
    <div class="col-md-6 col-md-offset-3">
    <form id="transForm" class="well" v-on:submit.prevent="formSubmit">
      <input class="form-control" type="text" v-model="textToTranslate" placeholder="Enter a word...">

      <select class="form-control" v-model="language">
        <option value="ru">Russian</option>
        <option value="ko">Korean</option>
        <option value="es">Spanish</option>
        <option value="fr">French</option>
<!--
        <option value="">Chinese</option>
        <option value="">Arabic</optioin>
            -->
      </select>
      <br>
      <input class="btn btn-primary" type="submit" value="Translate">

    </form>
  </div>
  </div>
</template>

<script>
export default {
  name: 'translateForm',
  data(){
    return {
      textToTranslate:''
    }
  },
  created(){
    this.language = 'ko';
  },
  methods:{
  formSubmit(){
      this.$emit('formSubmit', this.textToTranslate, this.language);
    }
  }
}

</script>

<style>

#transForm{
  border-radius: 10px;
  border: 1px #ccc solid;
}

</style>
