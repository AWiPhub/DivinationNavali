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
          v-for="card in filteredList " :key="card.id"
          v-on:click="selectCard(card.name, card.id)"
        >
          {{ card.name }}
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
  background-color: #1e2124;
  width: 514px;
  margin-top: 1px;
  height: 35px;
}
.inputArea input, input::placeholder{
  width: 510px;
  height: 30px;
  background-color: #1e2124;
  color: #DFCF99;
  font-family: "PoEFont";
  font-size: 16px;
  text-align: center;
}
.visible{
  display: block;
  overflow:auto;
  scrollbar-width: 200px;
  overflow-x: hidden;
  scroll-behavior: smooth;
  height: 300px;
  z-index: 3;
  position: relative;
}
.visible button{
  width: 514px;
  height: 25px;
  background-color: #1e2124;
  color: #DFCF99;
  font-family: "PoEFont";
  cursor: pointer;
  border-right: none;
  border-top: none;
  border-bottom: none;
  border-left-color: #DFCF99;
  z-index: 4;
  margin-top: -1px;
}
.visible button:hover{
  background-color: #a8a8a8;
  color: #141414;
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
        { name: "Destined to Crumble", id: 33},
        { name: "Dialla's Subjugation", id: 34},
        { name: "Divine Justice", id: 35},
        { name: "Doedre's Madness", id: 36},
        { name: "Earth Drinker", id: 37},
        { name: "Echoes of Love", id: 38},
        { name: "Emperor of Purity", id: 39},
        { name: "Emperor's Luck", id: 40},
        { name: "Etched in Blood", id: 41},
        { name: "Forbidden Power", id: 42},
        { name: "Friendship", id: 43},
        { name: "Gemcutter's Promise", id: 44},
        { name: "Gift of the Gemling Queen", id: 45},
        { name: "Glimmer of Hope", id: 46},
        { name: "Grave Knowledge", id: 47},
        { name: "Harmony of Souls", id: 48},
        { name: "Her Mask", id: 49},
        { name: "Heterochromia", id: 50},
        { name: "Hope", id: 51},
        { name: "House of Mirrors", id: 52},
        { name: "Hubris", id: 53},
        { name: "Humility", id: 54},
        { name: "Hunter's Resolve", id: 55},
        { name: "Hunter's Reward", id: 56},
        { name: "Immortal Resolve", id: 57},
        { name: "Imperial Legacy", id: 58},
        { name: "Jack in the Box", id: 59},
        { name: "Lantador's Lost Love", id: 60},
        { name: "Last Hope", id: 61},
        { name: "Left to Fate", id: 62},
        { name: "Light and Truth", id: 63},
        { name: "Lingering Remnants", id: 64},
        { name: "Lost Worlds", id: 65},
        { name: "Loyalty", id: 66},
        { name: "Lucky Connections", id: 67},
        { name: "Lucky Deck", id: 68},
        { name: "Lysah's Respite", id: 69},
        { name: "Mawr Blaidd", id: 70},
        { name: "Merciless Armament", id: 71},
        { name: "Might is Right", id: 72},
        { name: "Mitts", id: 73},
        { name: "Monochrome", id: 74},
        { name: "More is Never Enough", id: 75},
        { name: "No Traces", id: 76},
        { name: "Nook's Crown", id: 77},
        { name: "Perfection", id: 78},
        { name: "Pride Before the Fall", id: 79},
        { name: "Pride of the First Ones", id: 80},
        { name: "Prosperity", id: 81},
        { name: "Rain of Chaos", id: 82},
        { name: "Rain Tempter", id: 83},
        { name: "Rats", id: 84},
        { name: "Rebirth", id: 85},
        { name: "Remembrance", id: 86},
        { name: "Sambodhi's Vow", id: 87},
        { name: "Scholar of the Seas", id: 88},
        { name: "Seven Years Bad Luck", id: 89},
        { name: "Shard of Fate", id: 90},
        { name: "Squandered Prosperity", id: 91},
        // { name: "Struck by Lightning", id: 92},
        // { name: "Succor of the Sinless", id: 93},
        // { name: "The Admirer", id: 94},
        // { name: "The Aesthete", id: 95},
        // { name: "The Archmage's Right Hand", id: 96},
        // { name: "The Arena Champion", id: 97},
        // { name: "The Army of Blood", id: 98},
        // { name: "The Artist", id: 99},
        // { name: "The Avenger", id: 100},
        // { name: "The Bargain", id: 101},
        // { name: "The Battle Born", id: 102},
        // { name: "The Beast", id: 103},
        // { name: "The Betrayal", id: 104},
        // { name: "The Blazing Fire", id: 105},
        // { name: "The Body", id: 106},
        // { name: "The Bones", id: 107},
        // { name: "The Breach", id: 108},
        // { name: "The Brittle Emperor", id: 109},
        // { name: "The Cacophony", id: 110},
        // { name: "The Calling", id: 111},
        // { name: "The Carrion Crow", id: 112},
        // { name: "The Cartographer", id: 113},
        // { name: "The Cataclysm", id: 114},
        // { name: "The Catalyst", id: 115},
        // { name: "The Celestial Justicar", id: 116},
        // { name: "The Celestial Stone", id: 117},
        // { name: "The Chains that Bind", id: 118},
        // { name: "The Cheater", id: 119},
        // { name: "The Chosen", id: 120},
        // { name: "The Coming Storm", id: 121},
        // { name: "The Conduit", id: 122},
        // { name: "The Craving", id: 123},
        // { name: "The Cursed King", id: 124},
        // { name: "The Damned", id: 125},
        // { name: "The Dapper Prodigy", id: 126},
        // { name: "The Dark Mage", id: 127},
        // { name: "The Darkest Dream", id: 128},
        // { name: "The Deal", id: 129},
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
      var comp = this.search.toLowerCase();
      return this.users.filter(function (elem) {
        if(comp==='') return true;
        else return elem.name.toLowerCase().indexOf(comp) > -1;
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
  card("Destined to Crumble", 33),
  card("Dialla's Subjugation", 34),
  card("Divine Justice", 35),
  card("Doedre's Madness", 36),
  card("Earth Drinker", 37),
  card("Echoes of Love", 38),
  card("Emperor of Purity", 39),
  card("Emperor's Luck", 40),
  card("Etched in Blood", 41),
  card("Forbidden Power", 42),
  card("Friendship", 43),
  card("Gemcutter's Promise", 44),
  card("Gift of the Gemling Queen", 45),
  card("Glimmer of Hope", 46),
  card("Grave Knowledge", 47),
  card("Harmony of Souls", 48),
  card("Her Mask", 49),
  card("Heterochromia", 50),
  card("Hope", 51),
  card("House of Mirrors", 52),
  card("Hubris", 53),
  card("Humility", 54),
  card("Hunter's Resolve", 55),
  card("Hunter's Reward", 56),
  card("Immortal Resolve", 57),
  card("Imperial Legacy", 58),
  card("Jack in the Box", 59),
  card("Lantador's Lost Love", 60),
  card("Last Hope", 61),
  card("Left to Fate", 62),
  card("Light and Truth", 63),
  card("Lingering Remnants", 64),
  card("Lost Worlds", 65),
  card("Loyalty", 66),
  card("Lucky Connections", 67),
  card("Lucky Deck", 68),
  card("Lysah's Respite", 69),
  card("Mawr Blaidd", 70),
  card("Merciless Armament", 71),
  card("Might is Right", 72),
  card("Mitts", 73),
  card("Monochrome", 74),
  card("More is Never Enough", 75),
  card("No Traces", 76),
  card("Nook's Crown", 77),
  card("Perfection", 78),
  card("Pride Before the Fall", 79),
  card("Pride of the First Ones", 80),
  card("Prosperity", 81),
  card("Rain of Chaos", 82),
  card("Rain Tempter", 83),
  card("Rats", 84),
  card("Rebirth", 85),
  card("Remembrance", 86),
  card("Sambodhi's Vow", 87),
  card("Scholar of the Seas", 88),
  card("Seven Years Bad Luck", 89),
  card("Shard of Fate", 90),
  card("Squandered Prosperity", 91),
  // card("Struck by Lightning", 92),
  // card("Succor of the Sinless", 93),
  // card("The Admirer", 94),
  // card("The Aesthete", 95),
  // card("The Archmage's Right Hand", 96),
  // card("The Arena Champion", 97),
  // card("The Army of Blood", 98),
  // card("The Artist", 99),
  // card("The Avenger", 100),
  // card("The Bargain", 101),
  // card("The Battle Born", 102),
  // card("The Beast", 103),
  // card("The Betrayal", 104),
  // card("The Blazing Fire", 105),
  // card("The Body", 106),
  // card("The Bones", 107),
  // card("The Breach", 108),
  // card("The Brittle Emperor", 109),
  // card("The Cacophony", 110),
  // card("The Calling", 111),
  // card("The Carrion Crow", 112),
  // card("The Cartographer", 113),
  // card("The Cataclysm", 114),
  // card("The Catalyst", 115),
  // card("The Celestial Justicar", 116),
  // card("The Celestial Stone", 117),
  // card("The Chains that Bind", 118),
  // card("The Cheater", 119),
  // card("The Chosen", 120),
  // card("The Coming Storm", 121),
  // card("The Conduit", 122),
  // card("The Craving", 123),
  // card("The Cursed King", 124),
  // card("The Damned", 125),
  // card("The Dapper Prodigy", 126),
  // card("The Dark Mage", 127),
  // card("The Darkest Dream", 128),
  // card("The Deal", 129),
]
</script>