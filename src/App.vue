<template>
  <div id="app">
    <p>
      Welcome to your Vue.js app with dropzone!
    </p>
    <dropzone id="myVueDropzone" url="https://httpbin.org/post" v-on:vdropzone-success="success"></dropzone>
  </div>
</template>

<script>
  import Dropzone from '../src/index'
  export default {
    name: 'MainApp',
    components: {
      Dropzone
    },
    data () {
      return {
        processQueue: false,
        fa: true
      }
    },
    methods: {
      'success': function (file) {
        console.log('A file was successfully uploaded')
      },
      'process': function () {
        var newArr = this.$children.filter(function(item){
          return item.id === "myVueDropzone";
        });
        var component = newArr[0];
        component.processQueue()
      }
    }
  }
</script>

<style scoped>
  @import url('~dropzone/dist/dropzone.css');
  @import 'https://fonts.googleapis.com/css?family=Roboto';
</style>