<template>
  <div class="home">
    <h1>Vue3 Crud Users</h1>
    <list></list>
  </div>
</template>

<script>
// @ is an alias to /src

import List from '../components/List'
export default {
  
  name: 'Home',
  components: {
    List
  }
}
</script>
