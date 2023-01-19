<template>
  <div class="tourCard">
    <h2>Tour Name</h2>
    <div class="tourDetails">
      <div class="detail">
        <div><span class="detailName">Time</span></div>
        <div><span class="detailData">5:45</span></div>
      </div>
      <div class="detail">
        <div><span class="detailName">Distance</span></div>
        <div><span class="detailData">13,6 km</span></div>
      </div>
      <div class="detail">
        <div><span class="detailName">Ascent</span></div>
        <div><span class="detailData">1420 m</span></div>
      </div>
      <div class="detail">
        <div><span class="detailName">Descent</span></div>
        <div><span class="detailData">450 m</span></div>
      </div>
    </div>
    <div class="tourDescription">
      Description of the tour. This will be lots of text and hopefully shortend if it's too long. We will see. 
    </div>
  </div>
</template>

<style scoped>
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
