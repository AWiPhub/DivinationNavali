<template>
  <div class="Divination-Cards">
    <div class="blockText">
      <h2 class="Title">
        <p>This is an Divination Cards page</p>
      </h2>
      <div class="content">
        <p>Select Divination Card</p>
        <div class="inputArea">
          <input
            v-model="name"
            placeholder="Enter your Divination Card..."
            v-on:click="visible = true"
          >
          <div v-show="visible">
            <button
              v-for="card in filteredList"
              v-on:click="SubmitChoice(card.name)"
            >
              {{ card.name }}
            </button>
          </div>
        </div>
      </div>
    </div>
    <showing-card :sltcd="search"></showing-card>
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

.inputArea{
  width: 200px;
}

input{
  width: 200px;
}

button{
  width: 200px;
}

ul{
  padding: 0 0 0 0;
}

li{
  border: solid 1px rgba(255, 255, 255, 0.2);
}

li:hover{
  cursor: pointer;
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
      cards: cards,
      visible: false,
      name: '',
      users: [
        { name: "Assassin's Favour" },
        { name: "The Inoculated" },
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
    SubmitChoice: function (message) {
      this.name = message;
      this.visible = false;
    }
  }
}


const card = (name) => ({name})

const cards = [
  card("Assassin's Favour"),
  card("The Inoculated")
]
</script>