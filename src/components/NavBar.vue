<script>
import LogoIcon from './icons/IconLogo.vue'

export default{
  components: {LogoIcon},
}
</script>

<template>
  <div class="navBar">
    <div class="contents">
      <div class="logoIcon">
        <LogoIcon></LogoIcon>
      </div>
      
      <div class="logo">
        HikeReport
      </div>
      <div class="newTour">
        <button @click="$emit('openModal')">+ New Tour</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
.navBar {
  width: 100%;
  height: 70px;
  background-color: rgb(255, 255, 255);
  box-shadow: 0px 0px 6px rgb(202, 202, 202);
  margin-bottom: 20px;
}
.contents {
  max-width: 1000px;
  height: 70px;
  display: flex;
  flex-direction: row;
  align-items: center;
  min-width: 286px;
}
.logoIcon{
  flex-grow: 0;
  padding-left: 12px;
  margin-top: 4px;
}
.logo {
  flex-grow: 4;
  padding: 12px;
  color: rgb(0, 183, 255);
  font-size: larger;
  font-weight: bold;
}
.newTour {
  flex-grow: 4;
  text-align: right;
  padding: 12px;
}
  
button{
  background-color: rgb(0, 183, 255);
  border-radius: 20px;
  padding: 6px 12px 6px 12px;
  color: white;
  font-weight: bold;
  text-decoration: none;
  border: none;
  font-size: 1em;
}
button:hover{
  cursor: pointer;
}

@media (min-width: 1024px) {
  .contents {
  margin: 0 auto;
  font-weight: normal;
}
}
</style>
