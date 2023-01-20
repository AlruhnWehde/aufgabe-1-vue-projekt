<script>
import Tour from './Tour.vue'

export default{
  components: { Tour},
  props: ['data']
}
</script>

<template>
  <div class="contents">
    <h1>All Reports</h1>
    
    <div v-for="element in data.slice().reverse()" :key="element" >
      <Tour :title="element[0]" :hours="element[1]" :min="element[2]" :distance="element[3]" :ascent="element[4]" :descent="element[5]">
        {{element[6]}}
    </Tour>
    </div>

    <div class="endOfTours">That's all the reports for now.</div>
  </div>
</template>

<style scoped>
.contents {
  max-width: 1000px;
  padding: 12px;
  min-width: 400px;
  
}


.endOfTours{
  color: rgb(219, 219, 219);
  text-align: center;
  font-weight: bold;
  margin-bottom: 30px;
}

@media (min-width: 1024px) {
  .contents {
  margin: 0 auto;
  font-weight: normal;
}
}

</style>
