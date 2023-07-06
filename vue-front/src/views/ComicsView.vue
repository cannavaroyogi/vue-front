<template>
  <div class="home">
    <AppNavbar />
    <div class="container">
        <h1> Comics </h1>
    </div>
    
  </div>
</template>

<script>
// @ is an alias to /src
import AppNavbar from '@/components/AppNavbar.vue'

export default {
  name: 'ComicsView',
  components: {
    AppNavbar
  }
}
</script>