<template>
  <div class="Divination-Cards">
    <div class="blockText">
      <h2 class="Title">
        <p>This is an Divination Cards page</p>
      </h2>
    </div>

    <div class="inputArea">
      <input
        v-model="name"
        placeholder="Select Divination Card"
        v-on:click="visible = true"
        onclick="this.select();"
      >
      <div v-show="visible" class="visible">
        <button
          v-for="(card, index) in filteredList" :key="card.index"
          v-on:click="SubmitChoice(card.name, index)"
        >
          {{ card.name }} - {{ index }}
        </button>
      </div>
    </div>

    <showing-card v-bind:ind="index"></showing-card>
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
      index: '',
      users: [
        { name: "A Dab of Ink"},
        { name: "A Mother's Parting Gift"},
        { name: "Abandoned Wealth"},
        { name: "Akil's Prophecy"},
        { name: "Alluring Bounty"},
        { name: "Alone in the Darkness"},
        { name: "Anarchy's Price"},
        { name: "Arrogance of the Vaal"},
        { name: "Assassin's Favour"},
        { name: "Atziri's Arsenal"},
        { name: "Audacity"},
        { name: "Azyran's Reward"},
        { name: "Baited Expectations"},
        { name: "Beauty Through Death"},
        { name: "Blessing of God"},
        { name: "Blind Venture"},
        { name: "Boon of Justice"},
        { name: "Boon of the First Ones"},
        { name: "Boundless Realms"},
        { name: "Bowyer's Dream"},
        { name: "Buried Treasure"},
        { name: "Burning Blood"},
        { name: "Call to the First Ones"},
        { name: "Cameria's Cut"},
        { name: "Cartographer's Delight"},
        { name: "Chaotic Disposition"},
        { name: "Council of Cats"},
        { name: "Coveted Possession"},
        { name: "Dark Dreams"},
        { name: "Dark Temptation"},
        { name: "Death"},
        { name: "Deathly Designs"},
        { name: "Demigod's Wager"},
        { name: "Dialla's Subjugation"},
        { name: "Divine Justice"},
        { name: "Doedre's Madness"},
        { name: "Earth Drinker"},
        { name: "Echoes of Love"},
        { name: "Emperor of Purity"},
      ]
    }
  },
  computed:{
    filteredList: function(){
      var comp = this.name;
      return this.users.filter(function (elem) {
        if(comp==='') return true;
        else return elem.name.indexOf(comp) > -1;
      })
    }
  },
  methods: {
    SubmitChoice: function (message, index) {
      this.name = message;
      this.visible = false;
      this.index = index;
    }
  }
}

const card = (name) => ({name})

const cards = [
  card("A Dab of Ink"),
  card("A Mother's Parting Gift"),
  card("Abandoned Wealth"),
  card("Akil's Prophecy"),
  card("Alluring Bounty"),
  card("Alone in the Darkness"),
  card("Anarchy's Price"),
  card("Arrogance of the Vaal"),
  card("Assassin's Favour"),
  card("Atziri's Arsenal"),
  card("Audacity"),
  card("Azyran's Reward"),
  card("Baited Expectations"),
  card("Beauty Through Death"),
  card("Blessing of God"),
  card("Blind Venture"),
  card("Boon of Justice"),
  card("Boon of the First Ones"),
  card("Boundless Realms"),
  card("Bowyer's Dream"),
  card("Buried Treasure"),
  card("Burning Blood"),
  card("Call to the First Ones"),
  card("Cameria's Cut"),
  card("Cartographer's Delight"),
  card("Chaotic Disposition"),
  card("Council of Cats"),
  card("Coveted Possession"),
  card("Dark Dreams"),
  card("Dark Temptation"),
  card("Death"),
  card("Deathly Designs"),
  card("Demigod's Wager"),
  card("Dialla's Subjugation"),
  card("Divine Justice"),
  card("Doedre's Madness"),
  card("Earth Drinker"),
  card("Echoes of Love"),
  card("Emperor of Purity"),
  
]
</script>