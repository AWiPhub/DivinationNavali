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
          v-for="(card, index) in filteredList"
          v-on:click="SubmitChoice(card.name, index)"
        >
          {{ card.name }}
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
        { name: "Assassin's Favour"},
        { name: "The Inoculated"},
        { name: "The Lunaris Priestess"},
        { name: "The Watcher"},
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
  card("Assassin's Favour"),
  card("The Inoculated"),
  card("The Lunaris Priestess"),
  card("The Watcher"),
]
</script>