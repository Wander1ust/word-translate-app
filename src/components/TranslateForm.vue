<template>
  <div id="translateForm">
  <div class="row justify-content-center align-items-center h-100">
        <form id="transForm"class="form-inline well" v-on:submit="formSubmit">
            <input class="form-control" type="text" v-model="textToTranslate" placeholder="Enter a word..">
            <select class="form-control" v-model="language">
                <option value="ga">Irish</option>
                <option value="cy">Welsh</option>
                <option value="gd">Scottish</option>
            </select>
            
            <input class="btn btn-primary"type="submit" value="Translate">
        </form>
        </div>
        </div>
</template>

<script>

export default {
  name: 'translateForm',
  date(){
      return {
          textToTranslate:'',
          language:''
      }
  },
  created() {
      this.language = 'ga';
  },
  methods: {
      formSubmit(e){
        this.$emit('formSubmit', this.textToTranslate, this.language);
          e.preventDefault();
      }
  }
}
</script>

<style>
    #transForm{
        border-radius:10px;
        border: 1px #ccc solid;
    }
</style>
