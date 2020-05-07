<template>
  <div class="Divination-Cards">
    <div class="blockText">
      <h2 class="Title">
        <p>This is an Divination Cards page</p>
      </h2>
      <div class="content">
        <p>Select Divination Card</p>
      
        <select v-model="SelectedCard">
          <option
          v-for="card in cards"
          v-on:change="selectCard"
          >
            {{ card.name }}
          </option>
        </select>
      </div>
    </div>
    <showing-card :sltcd="SelectedCard"></showing-card>
  </div>
</template>

<style scoped>
.blockText {
  margin: 13px 0px 0px;
  border: 1px solid;
  border-color: #141414;
  padding: 6px;
  background-color: #0c0b0b;
  position: relative;
  width: 500px;
}
h2{
  color: #DFCF99;
  font-size: 16.9px;
}

.content p{
  color: #A38D6D;
  font-size: 15px;
}
</style>

<script>
import ShowingCard from '../components/ShowingCard.vue' // ПОДКЛЮЧЕНИЕ КОМПОНЕНТА 1

export default {
  props: {
    SelectedCard: String
  },
  components:{ // ПОДКЛЮЧЕНИЕ КОМПОНЕНТА 2
    ShowingCard
  },
  data() {
    return{
      cards: cards
    }
  },
  methods: {
    selectCard: function() {
      console.log('click')
    }
  }
}



const card = (name) => ({name})

const cards = [
  card("Assassin's Favour"),
  card("The Inoculated")
]


</script>