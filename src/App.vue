<script>
import NavBar from './components/NavBar.vue'
import TourPosts from './components/TourPosts.vue'
import Modal from './components/NewTourModal.vue'

export default{
  components: { NavBar, TourPosts, Modal},

  data() {
    return {
      showModal: false,
      tourList : [
        ["Tour example number one", "1", "34", "4.5", "345", "345", "this is the description of the tour"], 
        ["Second tour example", "2", "45", "12.7", "540", "540", "this is the description of the tour with more text and stuff that goes here. Maybe even makes it two lines"], 
        ["Another tour example here", "6", "24", "14.2", "1230", "1230", "this is another the description of another tour"],
        ["The newest tour example", "6", "24", "14.2", "1230", "1230", "Now please post your own tours so this looks more alive. :)"]
      ]
    }
  },
  methods: {
    addNewTour(newTour){
      this.tourList.push(newTour);
    }
  }
}

</script>


<template>
  <!-- modal basics from https://vuejs.org/examples/#modal -->
  <Teleport to="body">
    <modal :show="showModal" @close="showModal = false" 
      @publishTour='(title, hours, min, distance, ascent, descent, description) => {
        addNewTour([title, hours, min, distance, ascent, descent, description]); 
        showModal = false
      }'
    >
    </modal>
  </Teleport>

    <NavBar id="show-modal" @openModal="showModal = true"></NavBar>
    <TourPosts :data="tourList"></TourPosts>
    
</template>