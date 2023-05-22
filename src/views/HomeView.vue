<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <Info msg="Welcome to our exam work"/>
  </div>
</template>

<script>
// @ is an alias to /src
import Info from '@/components/Info.vue'

export default {
  name: 'HomeView',
  components: {
    Info
  }
}
</script>
