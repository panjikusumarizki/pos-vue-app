<template>
  <div class="home">
    <navbar/>
    <contents/>
  </div>
</template>

<script>
import Navbar from '../components/Navbar'
import Content from '../components/Content'

export default {
  components: {
    navbar: Navbar,
    contents: Content
  }
}
</script>
