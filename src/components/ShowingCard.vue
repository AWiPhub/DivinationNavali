<template>
  <div class="ShowingCard">
    <button
      v-on:click="check(ind)"
      class="GoSearch"
    >
      Search
    </button>
    <div class="divinationCard">
      <div class="cardFace">
        <img
          :src="require(`../images/divination-cards/${card.name}.png`)"
          :alt="card.name">
      </div>
      <div class="itemBoxContent">
        <div class="itemHeader">
          <p> {{ card.name }} </p>
        </div>
        <div class="itemStack">
          <p> {{ card.stack }} </p>
        </div>
        <div class="itemReward">
          <p> {{ card.reward }} </p>
        </div> 
        <div class="itemDescription">
          <p> {{ card.description }} </p>
        </div>
      </div>
    </div>    
  </div>
</template>


<style>
.GoSearch{
  background-color: #fff;
  position: absolute;
  margin-left: 194px;
  margin-top: -43px;
  height: 32px;
  background-color: #0c0b0b;
  font-family: "PoEFont";
  font-size: 16px;
  text-align: center;
  color: #DFCF99;
  border-right: none;
  border-top: none;
  border-bottom: none;
  cursor: pointer;
}

.backCard{
  height: 300px;
}

.itemBoxContent{
  background:  url("../images/divination-cards/divination-card-base.png") no-repeat center;
  background-size: cover;
  width: 100%;
  height: 100%;
}

.divinationCard { 
  padding-top: 20px;
  max-width: 268px;
  height: 401px;
  background: transparent;
  font-size: 14px;
  margin-top: 10px;
  margin-left: 23%;
}

.cardFace {
  z-index: -1;
  position: absolute;
  background: #1e1e1e;
  overflow: hidden;
  margin-top: 30px;
  margin-left: 16px;
}

.itemHeader{
  width: 74%;
  color: #111111;
  font-variant: small-caps;
  font-size: 16px;
  position: absolute;
  margin-top: -7px;
  margin-left: -55px;
  z-index: 2;
}

.itemStack{
  /* background-color: #fff; */
  width: 15%;
  height: 5%;
  position: absolute;
  color: #c8c8c8;
  margin-top: 34%;
  margin-left: 1.5%;
}

.itemReward{
  /* background-color: #fff; */
  width: 45%;
  height: 11%;
  font-variant: small-caps;
  font-size: 16.94px;
  position: absolute;
  color: #af6025;
  margin-top: 39%;
  margin-left: 19px;
}

.itemDescription{
  /* background-color: #fff; */
  width: 45%;
  margin-top: 53%;
  position: absolute;
  height: 18.5%;
  margin-left: 19px;
  color: #af6025;
  font-style: italic;
  font-size: 17px;
  font-variant: small-caps;
  line-height: 0.9;
}

.itemReward, .itemDescription{
  display: flex;
  justify-content: center; /*Центрирование по горизонтали*/
  align-items: center; 
}
</style>


<script>
const card = (name, pathImg, reward, stack, description) => ({name, pathImg, reward, stack, description})

const cards = [
  card("Assassin's Favour",
        "../images/divination-cards/Assassin's Favour.png",
        "Dagger",
        "9",
        "By the time their eyes meet,\
          the dark deal has long since been made,\
          and his fate long since sealed."),
  card("The Inoculated",
        "../images/divination-cards/The Inoculated.png",
        "Seraphim's Armour",
        "4",
        "Chaos spread, wreaking havoc and death.\
          They said none would be spared, and yet here I stand."),
  card("The Lunaris Priestess",
        "../images/divination-cards/The Lunaris Priestess.png",
        "Sire of Shards",
        "5",
        "Embrace the Light,\
          Await the Morrow,\
          No more Spite,\
          And no more Sorrow."),
  card("The Watcher",
        "../images/divination-cards/The Watcher.png",
        "Crown of Eyes",
        "12",
        "Strange eyes on top of spines\
          Gaze beyond the veil of time\
          Deep down below the mines\
          A dream of crimson and of grime"),
]


import SelectedCard from '../views/Divination-Cards.vue'

export default {
  props: ['ind'],
  data() {
    return{
      cards: cards,
      card: cards[0]
    }
  },
  methods: {
    check: function(ind) {
      this.card = cards[ind]
    }
  }
}
</script>