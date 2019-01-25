<template>
  <div class="hello">
    <span v-bind:title="message">鼠标悬停几秒钟查看此处动态绑定的提示信息！</span>
    <div class="show" v-if="seen">
        <h5>現在可以看到我了</h5>
        <ol>
          <li  v-for="item in items" :key="item.text">{{item.text}}</li>
        </ol>
        <label for="">請輸入您的姓名：</label>
        <input v-model.lazy="username" placeholder="姓名是？">
        <span>{{username}}</span>
    </div>
    <vegetables />
  </div>
</template>
<script>
import vegetables from './vegetables'
export default {
  name: 'HelloWorld',
  components:{
    vegetables
  },
  data () {
    return {
       message: '頁面加載於'+new Date().toLocaleString(),
       seen: true,
       items:[
          {text:'上班'},
          {text:'學習'},
          {text:'睡覺'},
       ],
       username:''
    };
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .show{
    width: 50%;
    margin-left: auto;
    margin-right: auto;
    height: 200px;
    border: 1px solid black;
  }
</style>
