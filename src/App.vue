<template>
  <div id="app">
    <!-- <img src="./assets/logo.png">
    <HelloWorld/> -->
    <h1>{{title}}</h1>
    <input v-model="newItem" v-on:keyup.enter="addNew">
    <ul>
        <li v-for="item in items" v-bind:class="{liClass: item.isFinished}" v-on:click="toggleFinish(item)">
          <!--
           v-on:click="toggleFinish(item)" item是v-for中循环的每一项

           -->
          {{item.label}}
        </li>
    </ul>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld'

export default {
  // name: 'App',
  // components: {
  //   HelloWorld
  // }
  data: function (){
    return {
      title: 'this is a todo list',
      items:[
      // {
      //   label: 'coding' ,
      //   isFinished: false
      // },
      // {
      //   label: 'Bool' ,
      //   isFinished: true
      // }
    ],
    newItem: '' //将newItem制空
      
    }  
  },
  methods: {
      toggleFinish: function(item){
        // console.log(item)
        item.isFinished = !item.isFinished
      },
      addNew: function() {
        // console.log(this.newItem)

        this.items.push({
          label: this.newItem,
          isFinished: false
        })
        this.newItem = '' //输入完后制空表单
      }
  }
}
</script>

<style>
.liClass{
  /*color: red;*/
  text-decoration: underline;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
