<script>
export default {
props:{
    name:String
  },
  inject:["username"]
}

</script>

<template>
   
      <h1 v-bind="$attrs">Hello {{name}}!</h1>
      <h1>Username {{username}}!</h1>
    
</template>

<style scoped>

</style>
