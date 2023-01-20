<script>
import { Transition } from 'vue';

export default {
    props: {
        title: String,
        hours: Number,
        min: Number,
        distance: Number,
        ascent: Number,
        descent: Number,
    },
    data() {
      return {
        show: false
      }
    },
    mounted() {
        this.show = true;
    },
    components: { Transition }
}
</script>

<template>
  <Transition>
  <div v-if="show" class="tourCard">
    <h2>{{title}}</h2>
    <div class="tourDetails">
      <div class="detail">
        <div><span class="detailName">Time</span></div>
        <div><span class="detailData">{{ hours }}:{{ min }}</span></div>
      </div>
      <div class="detail">
        <div><span class="detailName">Distance</span></div>
        <div><span class="detailData">{{ distance }} km</span></div>
      </div>
      <div class="detail">
        <div><span class="detailName">Ascent</span></div>
        <div><span class="detailData">{{ ascent }} m</span></div>
      </div>
      <div class="detail">
        <div><span class="detailName">Descent</span></div>
        <div><span class="detailData">{{ descent }} m</span></div>
      </div>
    </div>
    <div class="tourDescription">
      <slot></slot>
    </div>
  </div>
</Transition>
</template>

<style scoped>
.v-enter-active,
.v-leave-active {
  transition: opacity 1s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}

.tourCard{
  background-color: rgb(240, 240, 240);
  border-radius: 15px;
  padding: 20px;
  margin: 25px 0 25px 0;
}

.tourDetails{
  display: grid;
  grid-template-columns: auto auto auto auto;
}

.detail{
  line-height: 2em;
}
.detailName{
  font-weight: bold;
}
.detailData{
  background-color: rgb(147, 224, 255);
  border-radius: 10px;
  padding: 5px 10px 5px 10px;
}

.tourDescription{
  margin: 20px 0 10px 0;
}

</style>
