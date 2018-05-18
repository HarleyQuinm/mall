<template>
  <div id="app">
    <myheader></myheader>
    <components :is="pagename"></components>
  </div>
</template>

<script>
import myheader from './components/public/MyHeader'
import myhome from './components/MyHome'
export default {
  name: 'App',
  components: { 
    myheader,
    myhome
   },
   data(){
     return {
       pagename:myhome
     }
   }
}
</script>
<style scoped>
 #app{
   height: 100%;
 }
</style>



