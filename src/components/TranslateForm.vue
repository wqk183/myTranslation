<template>
  <div  id="translateForm">
      <div >
            <form id="transForm" @submit="formSubmit">
                <input  type="text" v-model="textToTranslate" placeholder="输入需要翻译的内容">
                <select v-model="language">
                    <option value="en">English</option>
                    <option value="ru">Russian</option>
                    <option value="ko">Korean</option>
                    <option value="ja">Janpenese</option>
                </select>
                <input  type="submit" value="翻译">
            </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'translateForm',
  data(){
      return{
          textToTranslate:"",
          language:""
      }
  },
  methods:{
      formSubmit(e){
          //alert(this.textToTranslate);
          this.$emit("formSubmit",this.textToTranslate,this.language);
          e.preventDefault();
      }
  },
  created(){
      this.language="en";
  }
  
}
</script>

<style scoped>
#transForm{
    border: 1px solid #ccc;
    border-radius: 10px;

}
</style>
