<template>
    <div id="food">
        <p> {{title}}</p>
        <p v-if='showSub'> {{subTitle}}</p>
        <div>
        <input type="text" v-model="mytodo">
        <button @click='handleClick'>addSomeThing</button>
        </div>
        <ul class="write">
            <li v-for='(todo,index) in todos' :key="index">{{todo}}<button v-on:click="deleteList">删除</button></li>
        </ul>
        <div v-bind:class="[myclass,fontclass]">設置字體大小
            <button v-on:click="changeCol">背景顯示隱藏</button>
            <button v-on:click="sayHello">alertHello</button>
        </div>
        <button v-on:click="show=!show">toggle</button>
       <template name="fade">
            <ul v-if="show">
                <li>one</li>
                <li>two</li>
                <li>three</li>
            </ul>
       </template>
    </div>
</template>
<script>
export default {
    name:'vegetables',
    data() {
        return{
            title:'hello vuejs',
            subTitle:'Vue React Angular is good',
            showSub:true,
            mytodo:'',
            todos:[],
            myclass:{changeColor:true},
            fontclass:{fontSize:true},
            show:true,
        }
    },
    methods:{
        handleClick(){
            this.todos.unshift(this.mytodo);
            this.mytodo = '';
            this.title = '您好，小程序';} ,
        changeCol:function(){
            this.myclass.changeColor=!this.myclass.changeColor,
            this.fontclass.fontSize=! this.fontclass.fontSize
        },
        sayHello:function(){
            alert('Hello Jone')
        },
        deleteList: function(index){
            this.todos.splice(index, 1)
            },
    },
    mounted() {
      this.sayHello()
      }
}

</script>
<style scoped>
    .write li{
        list-style: none;
    }
    .changeColor{
        width: 50%;
        height: 50px;
        margin-left: auto;
        margin-right: auto;
        border: 1px solid red;
        background-color: blueviolet;
    }
    .fontSize{
        font-size: 40px;
    }
    .fade-enter-active, .fade-leave-active {transition: opacity .5s;}
    .fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {opacity: 0;}
</style>

