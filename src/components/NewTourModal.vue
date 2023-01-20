<!-- basic structure taken from https://vuejs.org/examples/#modal -->
<script>
export default {
  props: {
    show: Boolean,
    showWarning: Boolean
  },
  data() {
    return {
      title: "",
      hours: "",
      min: "",
      distance: "",
      ascent: "",
      descent: "",
      description: "",
      showWarning: false
    };
  },
  methods: {
    submit(){
      // sorry, input validation could be better
      // with help from https://regexr.com/631qa
      var titleReg = /^.{3,120}$/;
      var descReg = /^.{9,}$/;
      var timeReg = /^\d{0,2}$/;
      var metersReg = /^\d{0,5}$/;
      var distReg = /^\d{0,3}(?:[.]\d{0,2})?$/;


      if(!this.title.match(titleReg) || !this.description.match(descReg) 
      || !this.hours.match(timeReg) || !this.min.match(timeReg) 
      || !this.distance.match(distReg) 
      || !this.ascent.match(metersReg) || !this.descent.match(metersReg)){
        this.showWarning = true;

      } else{

        if((this.hours + this.min <= 0) || this.distance <= 0 || this.ascent + this.descent <= 0)
        {
          this.showWarning = true;

        } else{

          //Make it pretty
          //I know, this is bad and it hurts, but it works
          if(this.hours.length == 1){
            this.hours = "0" + this.hours
          } else if(this.hours.length == 0){
            this.hours = "00"
          }

          if(this.min.length == 1){
            this.min = "0" + this.min
          } else if(this.min.length == 0){
            this.min = "00"
          }

          if(!this.distance.includes(".")){
            this.distance = this.distance + ".0"
          }

          this.$emit('publishTour', this.title, this.hours, this.min, this.distance, this.ascent, this.descent, this.description);
          this.title= "";
          this.hours= "";
          this.min= "";
          this.distance= "";
          this.ascent= "";
          this.descent= "";
          this.description= "";
          this.showWarning = false; 
          
        }
      }
    }
  }
}
</script>


<template>
<Transition name="modal">
    <div v-if="show" class="modal-mask">
      <div class="modal-container">
        <div class="modal-header">
          <h2>Post your Hike Report</h2>
        </div>

        <div class="modal-body">
          <div>Title</div>
          <input placeholder="Title of your hike" v-model="this.title">
          <div>Time (h:m)</div>
          <input id="hours" placeholder="hours" v-model="this.hours">
          <span> : </span>
          <input id="min" placeholder="minutes" v-model="this.min">
          <div>Distance (km)</div>
          <input id="distance" placeholder="kilometers" v-model="this.distance">
          <div>Ascent (m)</div>
          <input id="ascent" placeholder="meters up" v-model="this.ascent">
          <div>Descent (m)</div>
          <input id="descent" placeholder="meters down" v-model="this.descent">
          <div>Description</div>
          <textarea id="description" placeholder="Description of your hike" v-model="this.description"></textarea>
          <div v-if="showWarning" class="warning">Please check your Input.</div>
        </div>

        <div class="modal-footer">
            <button
              class="modal-publish-button"
              @click="submit"
            >Post Tour</button>
            <button
              class="modal-cancel-button"
              @click="$emit('close')"
            >Cancel</button> 
        </div>
      </div>
    </div>
  </Transition>
</template>


<style scoped>
.warning{
  color: rgb(255, 110, 110);
  font-weight: bold;
  text-align: center;
}
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  transition: opacity 0.3s ease;
}

.modal-container {
  width: 500px;
  margin: auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 15px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
}

.modal-header h3 {
  margin-top: 0;
}

.modal-body {
  margin: 20px 0;
}

.modal-footer button {
  float: right;
  margin-left: 10px;
  border-radius: 20px;
  padding: 8px 10px 8px 10px;
  text-decoration: none;
  border: none; 
  font-weight: bold;
  font-size: 0.9em;
}
.modal-footer button:hover{
  cursor: pointer;
}
.modal-cancel-button {
  background-color: rgb(138, 138, 138);
  color: white;
}
.modal-publish-button {
  background-color: rgb(0, 183, 255);
  color: white;
}

.modal-body input{
  width: 100%;
  padding: 5px;
  margin-bottom: 5px;
}
.modal-body input#min, .modal-body input#hours{
  width: 20%;
  min-width: 40px;
}
.modal-body textarea{
  width: 100%;
  padding: 5px;
  margin-bottom: 5px;
  font-family: inherit;
  font-size: 13.333px;
}

/*
 * The following styles are auto-applied to elements with
 * transition="modal" when their visibility is toggled
 * by Vue.js.
 *
 * You can easily play with the modal transition by editing
 * these styles.
 */

.modal-enter-from {
  opacity: 0;
}

.modal-leave-to {
  opacity: 0;
}

.modal-enter-from .modal-container,
.modal-leave-to .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}
</style>
