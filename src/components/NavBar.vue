<template>
  <div class="navBar">
    <div class="contents">
      <div class="logo">HikeReport</div>
      <div class="newTour">
        <a class="button" href="">+ New Tour</a>
      </div>
    </div>
  </div>
</template>

<style scoped>
.navBar {
  width: 100%;
  height: 50px;
  background-color: rgb(255, 255, 255);
  box-shadow: 0px 0px 6px rgb(202, 202, 202);
}
.contents {
  max-width: 1000px;
  height: 50px;
  display: flex;
  flex-direction: row;
  align-items: center;
  min-width: 255px;
}
.logo {
  flex-grow: 1;
  padding: 12px;
  color: rgb(0, 183, 255);
  font-weight: bold;
  font-size: larger;
}
.newTour {
  flex-grow: 1;
  text-align: right;
  padding: 12px;
}
  
.button{
  background-color: rgb(0, 183, 255);
  border-radius: 20px;
  padding: 6px 12px 6px 12px;
  color: white;
  font-weight: bold;
  text-decoration: none;
}

@media (min-width: 1024px) {
  .contents {
  margin: 0 auto;
  font-weight: normal;
}
}
</style>
