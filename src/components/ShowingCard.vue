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
          <span class="AllRewardInfo">
            <p v-bind:class="card.itemRarity"> {{card.reward}} </p>
            <p v-if="card.mapTier != 0"><span class="mapTier">Map Tier: </span><span class="mpTier">{{ card.mapTier }}</span></p>
            <p v-if="card.enchantment === true"><span class="enchantment">Eternal Labyrinth Enchantment</span> </p>
            <p v-if="card.itemLevel != 0"><span class="itemLevel">Item Level: </span><span class="iLvl">{{ card.itemLevel }}</span></p>
            <p v-if="card.quality != 0"><span class="quality">Quality: </span><span class="qualityNum"> +{{ card.quality }}% </span></p>
            <p v-if="card.timplicitcorrupted === true" class="timplicitcorrupted">Two-Implicit</p>
            <p v-if="card.corrupted === true" class="corrupted">Corrupted</p>
            <p v-if="card.influence != ''" class="Influence">{{card.influence}}</p>
          </span>
          
        </div> 
        <div class="itemDescription">
          <p> {{ card.description }} </p>
        </div>
        <!-- <div class="itemDropAreas">
          <p> {{ card.dropAreas }} </p>
        </div> -->
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
  z-index: 1;
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
  z-index: 2;
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
  z-index: 2;
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
  z-index: 2;
}

.itemReward, .itemDescription{
  display: flex;
  justify-content: center; /*Центрирование по горизонтали*/
  align-items: center; 
}

.AllRewardInfo{
  position: absolute;
  line-height: 0;
}
.Normal{
  color: rgb(200,200,200);
}
.Magic{
  color: #8888ff;
}
.Rare{
  color: rgb(255,255,119);
}
.Unic{
  color: rgb(175,96,37);
}
.Currency{
  color: rgb(170,158,130);
}
.Gem{
  color: rgb(27,162,155);
}
.Prophecy{
  color: rgb(181,75,255);
}
.mapTier, .itemLevel, .quality, .Influence{
  color: rgb(127,127,127);
}
.mpTier, .iLvl{
  color: rgb(200,200,200);
}
.enchantment{
  color: rgb(184,218,242);
}
.qualityNum{
  color: rgb(136,136,255);
}
.corrupted, .timplicitcorrupted{
  color: red;
}
</style>


<script>
const card = (name, reward, itemRarity, mapTier, enchantment, itemLevel, quality, timplicitcorrupted, corrupted, influence, stack, description, dropAreas, additionalDropRestrictions) => ({name, reward, itemRarity, mapTier, enchantment, itemLevel, quality, timplicitcorrupted, corrupted, influence, stack, description, dropAreas, additionalDropRestrictions})

const cards = [
  card("A Dab of Ink",
        "The Poet's Pen",
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "9",
        "The Poet's blood is the Empire's ink.",
        "The Library, Academy Map, Museum Map, Scriptorium Map",
        "N/A"),
  card("A Mother's Parting Gift",
        "Fertile Mind",
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "6",
        "Nature was her domain,\
          Love was her song,\
          Family was her devotion,\
          Knowledge was her gift.",
        "The Imperial Gardens, The High Gardens",
        "N/A"),
  card("Abandoned Wealth",
        "3x Exalted Orb",
        'Currency', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "5",
        "When the world burned, the greedy burned with it, while the clever left as paupers.",
        "Arsenal Map, Precinct Map, Mao Kun",
        "N/A"),
  card("Akil's Prophecy",
        "Fated Unique Item",
        'Prophecy', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "3",
        "The hatungo know many answers to the same question,\
          for time itself is a tangled web.",
        "N/A",
        "N/A"),
  card("Alluring Bounty",
        "10x Exalted Orb",
        'Currency', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "7",
        "A treasure worth killing for\
          is a treasure worth dying for.",
        "The Apex of Sacrifice • The Alluring Abyss",
        "N/A"),
  card("Alone in the Darkness",
        "Delve Item",
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "5",
        '"Sometimes, the most beautiful treasures...are the ones you cannot have."\
          - Beryl, Survivor from the Azurite Mines',
        "N/A",
        "Can drop from an Abyssal Trove."),
  card("Anarchy's Price",
        "Voltaxic Rift",
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        true, // Corrupted?
        "", // Influence?
        "13",
        "Born of relentless fury and abhorrence, warped by turmoil and anguish, tainted through desire and carnality, I thirst for bloodshed once more.",
        "N/A",
        "This item can drop from Rogue Exiles and the prophecy chain Anarchy's End."),
  card("Arrogance of the Vaal",
        "Item",
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        true, // Two-Implicit Corrupted?
        true, // Corrupted?
        "", // Influence?
        "8",
        "Discovery can lead to beauty, or it can lead to ruin.",
        "Ancient City Map • Sunken City Map",
        "N/A"),
  card("Assassin's Favour",
        "Dagger",
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "9",
        "By the time their eyes meet,\
          the dark deal has long since been made,\
          and his fate long since sealed.",
        "The Marketplace, The Quay, Alleyways Map, Arcade Map, Bazaar Map, Park Map, Port Map",
        "N/A"),
  card("Atziri's Arsenal",
        "Weapon",
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        true, // Corrupted?
        "", // Influence?
        "4",
        "In the prison of all sins, will you grasp godhood or sorrow? Only hope lies under the shadows.",
        "Vaults of Atziri",
        "N/A"),
  card("Audacity",
        "Doryani's Fist",
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        true, // Corrupted?
        "", // Influence?
        "5",
        "A jolt, and it moves. Or smolders.\
          A current, and it lives. Or dies.\
          A surge, and it transcends.\
          Or... not.\
          Only one way to find out.",
        "The Apex of Sacrifice",
        "N/A"),
  card("Azyran's Reward",
        "Prismatic Jewel",
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        true, // Corrupted?
        "", // Influence?
        "9",
        "Method transcends shape and size. Do something in parallel long enough, and you will always find\
          another way.",
        "Relic Chambers Map",
        "N/A"),
  card("Baited Expectations",
        "Fishing Item",
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "8",
        "The line between having not enough to do and too much to do is unusually fine.",
        "N/A",
        "N/A"),
  card("Beauty Through Death",
        "Queen's Sacrifice",
        'Prophecy', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "5",
        "Her beauty did not fade\
          her humanity did not survive.",
        "Vaal Temple Map",
        "K'aj A'alai"),
  card("Blessing of God",
        "Elreon's Jewellery",
        'Magic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        85, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "3",
        "When the darkness weighs upon you, grow light from within.",
        "N/A",
        "N/A"),
  card("Blind Venture",
        "Ring",
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        true, // Corrupted?
        "", // Influence?
        "7",
        "''It's risky not knowing where your wares come from. That's why I source my own.''\
          - Klayver, the Antiquarian",
        "The Reliquary (Act 5), The Reliquary (Act 10), Museum Map, Relic Chambers Map",
        "N/A"),
  card("Boon of Justice",
        "Offering to the Goddess",
        'Magic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "6",
        "Some gifts are obligations while others are simply opportunities.",
        "Chateau Map, Orchard Map, Plaza Map",
        "N/A"),
  card("Boon of the First Ones",
        "Bestiary Item",
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "6",
        "Wreathed in the skin and bones\
          of the beasts she slew,\
          her gift came from what she lost:\
          her humanity.",
        "Pit of the Chimera Map",
        "N/A"),
  card("Boundless Realms",
        "Map",
        'Magic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "4",
        "Boundless is the distance between where we start and where we start again.",
        "The Solaris Temple Level 1 (Act 8), The Solaris Temple Level 2 (Act 8), Ivory Temple Map, Temple Map",
        "N/A"),
  card("Bowyer's Dream",
        "Six-Link Harbinger Bow",
        'Magic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        91, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "6",
        "If this is my dream, I don't wish to wake.",
        "N/A",
        "Lord of the Ashen Arrow of Ashen Wood Map"),
  card("Buried Treasure",
        "Sulphite Scarab",
        'Magic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "3",
        "You can't seek riches without getting your hands dirty.",
        "Crystal Ore Map, Dig Map, Excavation Map, Flooded Mine Map, Geode Map",
        "N/A"),
  card("Burning Blood",
        "Xoph's Blood",
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        true, // Corrupted?
        "", // Influence?
        "6",
        "There's a place where up is down,\
          where right is wrong,\
          where pleasure is agony,\
          and where the living wish only for death.",
        "Lava Chamber Map, Forge of the Phoenix Map",
        "N/A"),
  card("Call to the First Ones",
        "Tier 1 Talisman",
        'Rare', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        true, // Corrupted?
        "", // Influence?
        "5",
        "The Ezomyte, desperate for aid, cried out to the gods.",
        "The Northern Forest (Act 7), Infested Valley Map",
        "N/A"),
  card("Cameria's Cut",
        "Scarab",
        'Magic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "2",
        "''There are two ways to pay, Gold and Blood. I'll take my share in both.''\
          -Cameria the Coldblooded",
        "N/A",
        "N/A"),
  card("Cartographer's Delight",
        "Map",
        'Normal', // Item Rarity?
        5, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "3",
        "A map is similar\
          to a pair of eyes,\
          without one you stumble\
          around, unable to find your way.",
        "The Harbour Bridge, The Foothills",
        "N/A"),
  card("Chaotic Disposition",
        "5x Chaos Orb",
        'Currency', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "1",
        "Life isn't what you make of it, it's already been made for you.",
        "Poorjoy's Asylum",
        "N/A"),
  card("Council of Cats",
        "Farrul Item",
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "4",
        "A King Loved By All,\
          A Shadow Awaiting Nightfall,\
          A Speaker Howling Away,\
          A Hunter Seeking Prey",
        "Hunter's Ambush",
        "N/A"),
  card("Coveted Possession",
        "5x Regal Orb",
        'Currency', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "9",
        "A taste of power brings a hunger for more.",
        "The Catacombs • The Ossuary (Act 5), The Ossuary (Act 10), Bone Crypt Map",
        "N/A"),
  card("Dark Dreams",
        "Bone Helmet",
        'Rare', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "Elder Item", // Influence?
        "4",
        "No one ever truly understood what she meant when she said she wanted to raise a family.",
        "N/A",
        "Drops from Minara Anemina."),
  card("Dark Temptation",
        "Obliteration",
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "5",
        "''Only a fool looks to the occult for power and expects to be spared from its wrath.''\
          - Voll, Emperor of Purity",
        "N/A",
        "Can also drop from hidden chests in The Azurite Mine."),
  card("Death",
        "Mon'tregul's Grasp",
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "4",
        "The end of the old,\
          the beginning of the new.\
          A unique opportunity for transformation,\
          for those with the power\
          to grasp it.",
        "The Karui Fortress • Bog Map, Flooded Mine Map, Marshes Map, Mud Geyser Map	",
        "N/A"),
  card("Deathly Designs",
        "Level 21 Trap Gem",
        'Gem', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        23, // X Quality?
        false, // Two-Implicit Corrupted?
        true, // Corrupted?
        "", // Influence?
        "7",
        "''The Karui was correct; there is virtue in honouring my ancestors.''",
        "N/A",
        "N/A"),
  card("Demigod's Wager",
        "Orb of Annulment",
        'Currency', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "7",
        "Sometimes you need to make your own luck.",
        "N/A",
        "The Cleansing Light of Basilica Map"),
  card("Destined to Crumble",
        "Body Armour",
        'Rare', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        100, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "5",
        "''Let us not forget the most important lesson the Vaal taught us:\
          Nothing is eternal.''\
          - Siosa Foaga, Imperial Scholar",
        "Academy Map, Museum Map, Scriptorium Map",
        "N/A"),
  card("Dialla's Subjugation",
        "Superior Support Gem",
        'Gem', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        23, // X Quality?
        false, // Two-Implicit Corrupted?
        true, // Corrupted?
        "", // Influence?
        "7",
        "A symbol of beauty and innocence\
          The gems corrupted her mind\
          Malachai corrupted her gems\
          All but a glimmer of\
          greatness lost in madness",
        "Ivory Temple Map, Temple Map",
        "N/A"),
  card("Divine Justice",
        "Helmet",
        'Unic', // Item Rarity?
        0, // X Map Tier?
        true, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "1",
        "Many sought the Goddess' blessing. Few survived the Labyrinth to receive it.",
        "Defiled Cathedral Map",
        "N/A"),
  card("Doedre's Madness",
        "Doedre Item",
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "9",
        "''Hold your tongue before I claim it.'' - Doedre Darktongue",
        "The Harvest (area), Doedre's Cesspool, Waste Pool Map",
        "Doedre or corresponding bosses"),
  card("Earth Drinker",
        "Granite Flask",
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "5",
        "Taste and grow strong. Drink too much and be buried.",
        "The Vastiri Desert, The Oasis, The Foothills, Desert Map, Dunes Map",
        "N/A"),
  card("Echoes of Love",
        "Fidelitas' Spike",
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        true, // Two-Implicit Corrupted?
        true, // Corrupted?
        "", // Influence?
        "3",
        "''I gave up my body for you. I gave up my name for you. And one day I shall give up my life for you.''",
        "Overgrown Ruin Map, Overgrown Shrine Map",
        "N/A"),
  card("Emperor of Purity",
        "Six-Link Holy Chainmail",
        'Magic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        60, // X Item Level?
        0, // X Quality?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        "", // Influence?
        "7",
        "True to his title,\
          Voll, newly crowned,\
          had many of the\
          Eternal Empire's signature\
          extravagances destroyed.",
        "The Western Forest (Act 6), The Chamber of Sins Level 1 (Act 7), The Chamber of Sins Level 2 (Act 7), Overgrown Ruin Map, Overgrown Shrine Map, Fungal Hollow Map",
        "N/A"),
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