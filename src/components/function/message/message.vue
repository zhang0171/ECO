<template>
  <div>
      <router-view :is='component' @changeSession='component="record"' @sendMsg='component="index"'></router-view>
  </div>
</template>
<script>
  import record from './record'
  import index from './index';
  export default {
    components: {
        index: index,
        record: record
    },
    data () {
      return {
        component: 'index'
      }
    }
  }
</script>

<style scoped> 
</style>
