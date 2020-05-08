<template>
  <div class="Divination-Cards">
    <div class="blockText">
      <h2 class="Title">
        <p>This is an Divination Cards page</p>
      </h2>
    </div>

    <div class="inputArea">
      <input
        v-model="search"
        placeholder="Select Divination Card"
        v-on:click="visible = true"
        onclick="this.select();"
      >
      <div v-show="visible" class="visible">
        <button
          v-for="card in filteredList " :key="card.index"
          v-on:click="selectCard(card.name, card.id)"
        >
          {{ card.name }} - {{ card.id }}
        </button>
      </div>
    </div>

    <showing-card v-bind:ind="id"></showing-card>
  </div>
</template>

<style scoped>
@font-face {
  font-family: "PoEFont";
  src: url("../fonts/Fontin-Regular.otf") format("truetype");
}
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
.inputArea{
  /* background-color: #fff; */
  width: 514px;
  margin-top: 5px;
  height: 35px;
}
.inputArea input, input::placeholder{
  width: 510px;
  height: 30px;
  background-color: #0c0b0b;
  color: #DFCF99;
  font-family: "PoEFont";
  font-size: 16px;
  text-align: center;
}
.visible{
  display: grid;
  overflow-y: scroll;
  overflow-x: hidden;
  scroll-behavior: smooth;
}
.visible button{
  width: 510px;
  height: 25px;
  background-color: #0c0b0b;
  color: #DFCF99;
  font-family: "PoEFont";
  cursor: pointer;
  z-index: 3;
}
</style>

<script>
import ShowingCard from '../components/ShowingCard.vue'
export default {
  props: {
    SelectedCard: String
  },
  components:{
    ShowingCard
  },
  data() {
    return{
      visible: false,
      name: '',
      search: '',
      id: 0,
      users: [
        { name: "A Dab of Ink", id: 0},
        { name: "A Mother's Parting Gift", id: 1},
        { name: "Abandoned Wealth", id: 2},
        { name: "Akil's Prophecy", id: 3},
        { name: "Alluring Bounty", id: 4},
        { name: "Alone in the Darkness", id: 5},
        { name: "Anarchy's Price", id: 6},
        { name: "Arrogance of the Vaal", id: 7},
        { name: "Assassin's Favour", id: 8},
        { name: "Atziri's Arsenal", id: 9},
        { name: "Audacity", id: 10},
        { name: "Azyran's Reward", id: 11},
        { name: "Baited Expectations", id: 12},
        { name: "Beauty Through Death", id: 13},
        { name: "Blessing of God", id: 14},
        { name: "Blind Venture", id: 15},
        { name: "Boon of Justice", id: 16},
        { name: "Boon of the First Ones", id: 17},
        { name: "Boundless Realms", id: 18},
        { name: "Bowyer's Dream", id: 19},
        { name: "Buried Treasure", id: 20},
        { name: "Burning Blood", id: 21},
        { name: "Call to the First Ones", id: 22},
        { name: "Cameria's Cut", id: 23},
        { name: "Cartographer's Delight", id: 24},
        { name: "Chaotic Disposition", id: 25},
        { name: "Council of Cats", id: 26},
        { name: "Coveted Possession", id: 27},
        { name: "Dark Dreams", id: 28},
        { name: "Dark Temptation", id: 29},
        { name: "Death", id: 30},
        { name: "Deathly Designs", id: 31},
        { name: "Demigod's Wager", id: 32},
        { name: "Dialla's Subjugation", id: 33},
        { name: "Divine Justice", id: 34},
        { name: "Doedre's Madness", id: 35},
        { name: "Earth Drinker", id: 36},
        { name: "Echoes of Love", id: 37},
        { name: "Emperor of Purity", id: 38},
      ]
    }
  },
  methods: {
    selectCard: function (message, index) {
      this.search = message;
      this.visible = false;
      this.id = index;
    }
  },
  computed:{
    filteredList: function(){
      var comp = this.search;
      return this.users.filter(function (elem) {
        if(comp==='') return true;
        else return elem.name.indexOf(comp) > -1;
      })
    }
  }
}
const card = (name, id) => ({name, id})
const cards = [
  card("A Dab of Ink", 0),
  card("A Mother's Parting Gift", 1),
  card("Abandoned Wealth", 2),
  card("Akil's Prophecy", 3),
  card("Alluring Bounty", 4),
  card("Alone in the Darkness", 5),
  card("Anarchy's Price", 6),
  card("Arrogance of the Vaal", 7),
  card("Assassin's Favour", 8),
  card("Atziri's Arsenal", 9),
  card("Audacity", 10),
  card("Azyran's Reward", 11),
  card("Baited Expectations", 12),
  card("Beauty Through Death", 13),
  card("Blessing of God", 14),
  card("Blind Venture", 15),
  card("Boon of Justice", 16),
  card("Boon of the First Ones", 17),
  card("Boundless Realms", 18),
  card("Bowyer's Dream", 19),
  card("Buried Treasure", 20),
  card("Burning Blood", 21),
  card("Call to the First Ones", 22),
  card("Cameria's Cut", 23),
  card("Cartographer's Delight", 24),
  card("Chaotic Disposition", 25),
  card("Council of Cats", 26),
  card("Coveted Possession", 27),
  card("Dark Dreams", 28),
  card("Dark Temptation", 29),
  card("Death", 30),
  card("Deathly Designs", 31),
  card("Demigod's Wager", 32),
  card("Dialla's Subjugation", 33),
  card("Divine Justice", 34),
  card("Doedre's Madness", 35),
  card("Earth Drinker", 36),
  card("Echoes of Love", 37),
  card("Emperor of Purity", 38),
  
]
</script>