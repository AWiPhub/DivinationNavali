<template>
  <div class="ShowingCard">
    <div class="divinationCard">
      <div class="cardFace">
        <img src="../images/divination-cards/Assassins Favor.png" alt="">
      </div>
      <div class="itemBoxContent">
        <div class="itemHeader">
          <p>{{ sltcd }}</p>
        </div>
        <div class="itemStack">
          <p v-for="card in cards" :key="card.name">
            {{card.stack}}
          </p>
        </div>
        <div class="itemReward">
          <p v-for="card in cards" :key="card.name">
            {{card.reward}}
          </p>
        </div>
        <div class="itemDescription">
          <p v-for="card in cards" :key="card.name">
            {{card.description}}
          </p>
        </div>
      </div>
    </div>    
  </div>
</template>

<style>
.backCard{
  height: 300px;
}

.itemBoxContent{
  z-index: 3;
  background:  url("../images/divination-cards/divination-card-base.png") no-repeat center;
  background-size: cover;
  width: 100%;
  height: 100%;
}
.divinationCard {
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
import SelectedCard from '../views/Divination-Cards.vue'

export default {
  props: ['sltcd'],
  data() {
    return {
      cards: [{
        name: "Assassin's Favour",
        reward: "Dagger",
        stack: '9',
        description: "By the time their eyes meet,\
                      the dark deal has long since been made,\
                      and his fate long since sealed."
      },
      {
        name: "Assassin's Favour",
        reward: "Seraphim's Armour",
        stack: '4',
        description: "Chaos spread, wreaking havoc and death.\
                      They said none would be spared, and yet here I stand."
      }
      ]
    }
  },
  computed: {
    allList: function() {
      return this.cards.filter(function (card){
        return card === {sltcd}
      })
    }
  },
}
</script>