<script>
import Tour from './Tour.vue'

export default{
  components: { Tour},

  data() {
    return {
      
    }
  }
}
</script>

<template>
  <div class="contents">
    <h1>All Reports</h1>
    
    <Tour></Tour>
    <Tour></Tour>
  </div>
</template>

<style scoped>
.contents {
  max-width: 1000px;
  padding: 12px;
  min-width: 312px;
}

@media (min-width: 1024px) {
  .contents {
  margin: 0 auto;
  font-weight: normal;
}
}

</style>
