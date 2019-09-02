<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <my-textarea/>
  </div>
</template>

<script>
  import MyTextarea from "./MyTextarea";
  export default {
    name: 'HelloWorld',
    components: {
      MyTextarea
      // MyTextarea
    },
    data () {
      return {
        msg: '可根据内容改变高度的textarea'
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
