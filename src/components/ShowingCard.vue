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
            <p v-if="card.watchstoneCount != 0"><span class="itemLevel">Watchstone Count: </span><span class="iLvl"> {{ card.watchstoneCount }}</span></p>
            <p v-if="card.timplicitcorrupted === true" class="timplicitcorrupted">Two-Implicit</p>
            <p v-if="card.unidentifiedCorrupted === true" class="corrupted">Unidentified Corrupted</p>
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
const card = (name, reward, itemRarity, mapTier, enchantment, itemLevel, quality, watchstoneCount, timplicitcorrupted, corrupted, unidentifiedCorrupted, influence, stack, description, dropAreas, additionalDropRestrictions) => ({name, reward, itemRarity, mapTier, enchantment, itemLevel, quality, watchstoneCount, timplicitcorrupted, corrupted, unidentifiedCorrupted, influence, stack, description, dropAreas, additionalDropRestrictions})

const cards = [
  card("A Dab of Ink",
        "The Poet's Pen",
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        true, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        true, // Two-Implicit Corrupted?
        true, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        true, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        true, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        true, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        true, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        true, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        true, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        true, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        true, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
        true, // Two-Implicit Corrupted?
        true, // Corrupted?
        false, // Unidentified Corrupted?
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
        0, // Watchstone Count?
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
  card("Emperor's Luck", // Name
        "5x Currency", // Reward
        'Currency', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "5", // X Stack
        "The house always wins.", // Description
        "The Imperial Gardens, The High Gardens, Courtyard Map, Orchard Map, Terrace Map", // Area Drops
        "N/A"),
  card("Etched in Blood", // Name
        "Rigwald's Quills", // Reward
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        true, // Two-Implicit Corrupted?
        true, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "9", // X Stack
        "When you strive to write your name on the dense pages of History, someone else, inevitably, must be crossed out.", // Description
        "N/A", // Area Drops
        "N/A"),
  card("Forbidden Power", // Name
        "Balefire", // Reward
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        true, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "4", // X Stack
        "Some things should not be used. Some power is too great a risk.", // Description
        "N/A", // Area Drops
        "N/A"),
  card("Friendship", // Name
        "A Master Seeks Help (Niko)", // Reward
        'Prophecy', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "3", // X Stack
        "''Set your life on fire. Seek those who fan your flames''\
          -Rumi of the Vaal", // Description
        "N/A", // Area Drops
        "N/A"),
  card("Gemcutter's Promise", // Name
        "Superior Gem", // Reward
        'Gem', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        20, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "3", // X Stack
        "''I swore to use my position to help the people. What good is power when it just accumulates on the already-powerful?'' - Erasmus, Imperial Gemcutter", // Description
        "The Ebony Barracks, The Lunaris Concourse, Colonnade Map, Promenade Map", // Area Drops
        "N/A"),
  card("Gift of the Gemling Queen", // Name
        "Level 20 Support Gem", // Reward
        'Gem', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "9", // X Stack
        "Our Lady Dialla,\
          as a symbol of our progress,\
          shines greater than all the gems.", // Description
        "The Tunnel, The Quarry, Crystal Ore Map, Dig Map, Excavation Map, Flooded Mine Map, Geode Map", // Area Drops
        "N/A"),
  card("Glimmer of Hope", // Name
        "Gold Ring", // Reward
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "8", // X Stack
        "When you dwell in total darkness, even the faintest light may guide you out.", // Description
        "The Cavern of Anger (Act 6), Flooded Mine Map, Underground Sea Map", // Area Drops
        "N/A"),
  card("Grave Knowledge", // Name
        "Summon Raging Spirit", // Reward
        'Gem', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        20, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "6", // X Stack
        "The dead tell me great insights. They've had nothing but time to sit and think.", // Description
        "The Ossuary (Act 10), Bone Crypt Map, Olmec's Sanctum, Cursed Crypt Map", // Area Drops
        "N/A"),
  card("Harmony of Souls", // Name
        "9x Shrieking Essence", // Reward
        'Currency', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "9", // X Stack
        "Shrieking souls locked away\
          Hate splits frozen cells asunder\
          The knot of corruption\
          undone at last", // Description
        "N/A", // Area Drops
        "This item can be acquired from map boss versions of the Act 9 Trio (Shavronne, Doedre, & Maligaro)"),
  card("Her Mask", // Name
        "Sacrifice Fragment", // Reward
        'Magic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "4", // X Stack
        "To her beauty you submit,\
          lest your neck the great Queen slit.", // Description
        "Alleyways Map, Ancient City Map, Arachnid Tomb Map, Arcade Map, Arid Lake Map, Armoury Map, Ashen Wood Map, Atoll Map, Barrows Map, Beach Map, Burial Chambers Map, Cage Map, Cells Map, Channel Map, City Square Map, Courtyard Map, Cursed Crypt Map, Desert Map, Excavation Map, Fields Map, Flooded Mine Map, Glacier Map, Grotto Map, Haunted Mansion Map, Ivory Temple Map, Jungle Valley Map, Leyline Map, Lookout Map, Marshes Map, Mausoleum Map, Maze Map, Mesa Map, Mud Geyser Map, Overgrown Ruin Map, Pen Map, Peninsula Map, Phantasmagoria Map, Pier Map, Primordial Pool Map, Promenade Map, Ramparts Map, Relic Chambers Map, Spider Lair Map, Fungal Hollow Map, Strand Map, Sulphur Vents Map, Thicket Map, Crater Map, Tropical Island Map, Waste Pool Map, Wharf Map", // Area Drops
        "Can drop in tier 1 to 6 maps."),
  card("Heterochromia", // Name
        "Two-Stone Ring", // Reward
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "2", // X Stack
        "Black and White, Silver and Gold\
          Let us see the world Unfold\
          Red and Blue, Yellow and Green\
          Let us remake it in colours Unseen", // Description
        "Estuary Map", // Area Drops
        "N/A"),
  card("Hope", // Name
        "Prismatic Ring", // Reward
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        true, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "2", // X Stack
        "The others succumbed to madness and depravity, but Lori fought on. Alone in the darkness, she could still see the dull light of hope's distant dawn.", // Description
        "Beach Map, Dungeon Map, Graveyard Map, Lookout Map", // Area Drops
        "N/A"),
  card("House of Mirrors", // Name
        "Mirror of Kalandra", // Reward
        'Currency', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "9", // X Stack
        "What do you see in the mirror?", // Description
        "The Alluring Abyss", // Area Drops
        "N/A"),
  card("Hubris", // Name
        "Ring", // Reward
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "5", // X Stack
        "''This one? It is NOT for sale. You would sooner pry it from my lifeless hand.''\
          - Jonfé Darontos, Ringmaker", // Description
        "The Library", // Area Drops
        "Can drop from Jeweller's Strongboxes."),
  card("Humility", // Name
        "Tabula Rasa", // Reward
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "9", // X Stack
        "", // Description
        "The Aqueduct, The Blood Aqueduct, Channel Map, Waterways Map", // Area Drops
        "N/A"),
  card("Hunter's Resolve", // Name
        "Bow", // Reward
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "8", // X Stack
        "Primed, curved and sleek.\
          Decisive and final.\
          For malice and righteousness.\
          There's but one solution.", // Description
        "The Riverways (Act 6), Ramparts Map, Fungal Hollow Map", // Area Drops
        "N/A"),
  card("Hunter's Reward", // Name
        "The Taming", // Reward
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "3", // X Stack
        "To tame a beast, you first must subdue its heart.", // Description
        "Grotto Map, The Putrid Cloister, Underground River Map", // Area Drops
        "N/A"),
  card("Immortal Resolve", // Name
        "Fated Connections", // Reward
        'Prophecy', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "6", // X Stack
        "The threads of fate are the strongest ties.", // Description
        "Carcass Map, Vault Map", // Area Drops
        "N/A"),
  card("Imperial Legacy", // Name
        "Six-Link Imperial Bow", // Reward
        'Normal', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        100, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "22", // X Stack
        "A life lost, A legacy born.", // Description
        "The Vastiri Desert, The Oasis, The Foothills, Desert Map, Desert Spring Map, Dunes Map, Pillars of Arun", // Area Drops
        "N/A"),
  card("Jack in the Box", // Name
        "Item", // Reward
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "4", // X Stack
        "Turn the crank,\
          close your eyes,\
          and pray to the gods\
          for a pleasant surprise.", // Description
        "The Ebony Barracks, The Slums, The Docks, The Sarn Ramparts, The Imperial Fields, The Harbour Bridge, The Grand Promenade, The Lunaris Concourse, The Quay, The Grain Gate, Arsenal Map, Ghetto Map, Port Map, Precinct Map, Promenade Map", // Area Drops
        "N/A"),
  card("Lantador's Lost Love", // Name
        "Two-Stone Ring", // Reward
        'Rare', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "7", // X Stack
        "They fought the storm together as one,\
          Until the longest of days was done.\
          Their love grew stronger\
          with every breath,\
          Until it was broken apart in death.", // Description
        "The Twilight Strand (Act 6), The Riverways (Act 6), The Wetlands (Act 6), The Southern Forest (Act 6), The Cavern of Anger (Act 6), The Beacon, The Brine King's Reef, The Coast (Act 6), The Tidal Island (Act 6), The Mud Flats (Act 6), The Karui Fortress, The Ridge, The Lower Prison (Act 6), Shavronne's Tower, Prisoner's Gate (Act 6), The Western Forest (Act 6), Maelström of Chaos, Lighthouse Map, Mineral Pools Map, Reef Map, Underground Sea Map", // Area Drops
        "N/A"),
  card("Last Hope", // Name
        "Mortal Hope", // Reward
        'Normal', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "3", // X Stack
        "As their civilisation crumbled, the Vaal looked to their queen. In her, they saw a way out. In them, she saw a burden she was happy to free herself from.", // Description
        "Vaal Temple Map", // Area Drops
        "N/A"),
  card("Left to Fate", // Name
        "Map", // Reward
        'Rare', // Item Rarity?
        16, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        true, // Unidentified Corrupted?
        "", // Influence?
        "4", // X Stack
        "Many strive for greatness,\
          but it is challenge, unforseen,\
          that forges heroes.", // Description
        "The Pale Court	", // Area Drops
        "N/A"),
  card("Light and Truth", // Name
        "Crystal Sceptre", // Reward
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "2", // X Stack
        "Time and change\
          shall naught avail,\
          To dim the Light\
          of Truth's fair grail.", // Description
        "The Upper Sceptre of God, Palace Map, Residence Map, Villa Map", // Area Drops
        "N/A"),
  card("Lingering Remnants", // Name
        "Vaal Temple Map", // Reward
        'Rare', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        83, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        true, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "16", // X Stack
        "Never dying, yet not living,\
          Endlessly they wander\
          beneath the harvest moon.", // Description
        "Acid Caverns Map, Arachnid Tomb Map, Arsenal Map, Basilica Map, Bog Map, Burial Chambers Map, Caldera Map, Carcass Map, Castle Ruins Map, Chateau Map, Pit of the Chimera Map, Colonnade Map, Colosseum Map, Core Map, Courthouse Map, Crimson Temple Map, Crystal Ore Map, Dark Forest Map, Defiled Cathedral Map, Desert Spring Map, Dig Map, Factory Map, Ghetto Map, Lair of the Hydra Map, Ivory Temple Map, Lair Map, Lava Lake Map, Malformation Map, Mesa Map, Maze of the Minotaur Map, Necropolis Map, Overgrown Shrine Map, Palace Map, Park Map, Forge of the Phoenix Map, Racecourse Map, Reef Map, Shrine Map, Siege Map, Summit Map, Sunken City Map, Terrace Map, Primordial Blocks Map, Tower Map, Villa Map", // Area Drops
        "Can drop from T11-T16 maps."),
  card("Lost Worlds", // Name
        "Map", // Reward
        'Normal', // Item Rarity?
        15, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "8", // X Stack
        "''There are worlds that lie beyond the edge of my page, the edge of my understanding. Worlds of wonder. Worlds of terror.'' Aramil - Cartographer to Emperor Chitus", // Description
        "N/A", // Area Drops
        "Sold by Zana at reputation level 4 or higher for 1x Orb of Chance"),
  card("Loyalty", // Name
        "3x Orb of Fusing", // Reward
        'Currency', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "5", // X Stack
        "Bound by fate,\
          inseparable by choice.", // Description
        "The Den (Act 7), Barrows Map, Grotto Map, Lair Map", // Area Drops
        "N/A"),
  card("Lucky Connections", // Name
        "20x Orb of Fusing", // Reward
        'Currency', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "7", // X Stack
        "Luck is a fool's game, and I know plenty of rich fools.", // Description
        "The Docks, The Quay, Pier Map, Port Map, Shipyard Map, Wharf Map", // Area Drops
        "N/A"),
  card("Lucky Deck", // Name
        "10x Stacked Deck", // Reward
        'Currency', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "9", // X Stack
        "When the outcome is the same, does it matter if it is fortune or trickery?", // Description
        "Ramparts Map, Mao Kun", // Area Drops
        "Also Shaped variants."),
  card("Lysah's Respite", // Name
        "Agate Amulet", // Reward
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        true, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "6", // X Stack
        "So many memories,\
          so much pain in\
          such a small token.\
          Drown it in blood\
          so you can forget.", // Description
        "Maelström of Chaos, Mineral Pools Map, Underground Sea Map", // Area Drops
        "N/A"),
  card("Mawr Blaidd", // Name
        "Eyes of the Greatwolf", // Reward
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "16", // X Stack
        "Rigwald believed he'd seized great power, but it was the great power that had seized Rigwald", // Description
        "Dark Forest Map", // Area Drops
        "N/A"),
  card("Merciless Armament", // Name
        "Merciless Two-Hand Weapon", // Reward
        'Magic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        100, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "4", // X Stack
        "''Through thick and thin,\
          blood and bone,\
          a peaceful life\
          is one I can't condone.''\
          - Tukohama, Father Of War", // Description
        "Armoury Map, Colonnade Map", // Area Drops
        "N/A"),
  card("Might is Right", // Name
        "Trypanon", // Reward
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "9", // X Stack
        "The mind had much to endure before the advent of thaumaturgy.", // Description
        "The Ossuary (Act 5), The Reliquary (Act 5), The Reliquary (Act 10), The Ossuary (Act 10), Mausoleum Map, Relic Chambers Map, Sepulchre Map", // Area Drops
        "N/A"),
  card("Mitts", // Name
        "Gloves", // Reward
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "5", // X Stack
        "Those whose hands are their livelihood know the importance of keeping them safe and warm.", // Description
        "The Ascent, The Solaris Temple Level 1 (Act 8), The Solaris Temple Level 2 (Act 8), Iceberg Map, Summit Map", // Area Drops
        "N/A"),
  card("Monochrome", // Name
        "10x Sextant", // Reward
        'Currency', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "3", // X Stack
        "''You cannot portray the world using just one colour. Together, you and I, we will paint our world into perfection.''\
          - Kyra, renegade thaumaturgist", // Description
        "Maelström of Chaos, The Vinktar Square, The Coward's Trial, Pillars of Arun, The Twilight Temple, Mao Kun, Whakawairua Tuahu, Poorjoy's Asylum, Oba's Cursed Trove, Vaults of Atziri", // Area Drops
        "N/A"),
  card("More is Never Enough", // Name
        "Gilded Scarab", // Reward
        'Normal', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "7", // X Stack
        "Greed is a hunger that only grows as you feed it", // Description
        "Infested Valley Map", // Area Drops
        "Gorulis, Will-Thief"),
  card("No Traces", // Name
        "30x Orb of Scouring", // Reward
        'Currency', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "9", // X Stack
        "There is no mistake so great that it cannot be undone.", // Description
        "The Ossuary (Act 5), The Reliquary (Act 10), The Ossuary (Act 10), Mausoleum Map, Relic Chambers Map, Sepulchre Map", // Area Drops
        "N/A"),
  card("Nook's Crown", // Name
        "Bone Helmet", // Reward
        'Rare', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        100, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "Elder Item", // Influence?
        "4", // X Stack
        "Every skull was once a person.\
          Though 'Who?' is rarely asked.\
          Friends, who wear\
          the crown of Nook,\
          Never need to ask.\
          They remember.", // Description
        "N/A", // Area Drops
        "Catarina, Master of Undeath in Mastermind's Lair"),
  card("Perfection", // Name
        "Jewellery", // Reward
        'Rare', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        100, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "Shaper Item", // Influence?
        "5", // X Stack
        "There are countless worlds, but only those with limitless potential will be able to achieve perfection.", // Description
        "Pit of the Chimera Map, Lair of the Hydra Map, Maze of the Minotaur Map, Forge of the Phoenix Map", // Area Drops
        "Drops from the Guardians of the Void."),
  card("Pride Before the Fall", // Name
        "Kaom's Heart", // Reward
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        true, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "8", // X Stack
        "As Kaom slew the last of his kin,\
          something deep inside him broke.\
          And through the cracks, corruption,\
          pure and black, spread forth.", // Description
        "The Coast (Act 6), The Tidal Island (Act 6), The Mud Flats (Act 6), The Karui Fortress, Caldera Map, Lava Lake Map, Marshes Map, Volcano Map", // Area Drops
        "N/A"),
  card("Pride of the First Ones", // Name
        "Farrul's Fur", // Reward
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "7", // X Stack
        "Upon silent paws and masked by the reeds,\
          Farrul's hunt begins as the light recedes.", // Description
        "Barrows Map, Grotto Map, Lair Map", // Area Drops
        "N/A"),
  card("Prosperity", // Name
        "Perandus' Gold Ring", // Reward
        'Magic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "10", // X Stack
        "Accumulating wealth has its own costs.", // Description
        "The Tidal Island (Act 6), Shore Map", // Area Drops
        "N/A"),
  card("Rain of Chaos", // Name
        "Chaos Orb", // Reward
        'Currency', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "8", // X Stack
        "Fire filled the sky that night\
          Chaos reigned\
          Where the shards fell\
          All was destroyed\
          -Jozen Kasigi, retelling an urban legend of the Cataclysm", // Description
        "The Crossroads (Act 7), The Imperial Fields, Castle Ruins Map", // Area Drops
        "N/A"),
  card("Rain Tempter", // Name
        "Strand Map", // Reward
        'Normal', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        73, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "9", // X Stack
        "Be like water, friend.", // Description
        "Grotto Map", // Area Drops
        "N/A"),
  card("Rats", // Name
        "Rat's Nest", // Reward
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "8", // X Stack
        "Whoever said 'more is always better' has obviously never met a rat.", // Description
        "The Imperial Fields, The Grain Gate, Arsenal Map, Factory Map", // Area Drops
        "N/A"),
  card("Rebirth", // Name
        "Charan's Sword", // Reward
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "27", // X Stack
        "He shattered Her smile\
          Scattered the fragments like ash\
          All she did was laugh", // Description
        "The Battlefront, The Slave Pens, The Ruined Square, The Desecrated Chambers, The Control Blocks (Act 10), The Reliquary (Act 10), The Ossuary (Act 10), The Broken Bridge (Act 7), The Crypt (Act 7), The Ashen Fields, The Blood Aqueduct, The Vastiri Desert, The Foothills, The Quarry", // Area Drops
        "N/A"),
  card("Remembrance", // Name
        "Precursor's Emblem", // Reward
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        true, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "8", // X Stack
        "''For all your struggles, all your achievements, even for the greatest of us, a story is all that remains. Write it well.''\
          -Julius Perandus, Father of Chitus", // Description
        "N/A", // Area Drops
        "N/A"),
  card("Sambodhi's Vow", // Name
        "Mortal Fragment", // Reward
        'Normal', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "3", // X Stack
        "He dispels dark realms\
          until mortal sufferings\
          yield to hopeful light.", // Description
        "N/A", // Area Drops
        "Can drop from members of the Immortal Syndicate."),
  card("Scholar of the Seas", // Name
        "Mao Kun", // Reward
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "7", // X Stack
        "I've never come upon a ship I could not command. I have however met sailors that were not willing to be led.", // Description
        "The Brine King's Reef, Coves Map, Reef Map", // Area Drops
        "N/A"),
  card("Seven Years Bad Luck", // Name
        "Mirror Shard", // Reward
        'Currency', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "13", // X Stack
        "If enough people believe something to be true, whether or not it is becomes irrelevant.", // Description
        "Defiled Cathedral Map	", // Area Drops
        "N/A"),
  card("Shard of Fate", // Name
        "Vivid Jewel", // Reward
        'Magic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        0, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        false, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "4", // X Stack
        "Their whims left unknown,\
          Their life left for others.", // Description
        "The Chamber of Sins Level 2 (Act 7), Museum Map, Overgrown Ruin Map, Overgrown Shrine Map", // Area Drops
        "N/A"),
  card("Squandered Prosperity", // Name
        "Perandus Manor", // Reward
        'Unic', // Item Rarity?
        0, // X Map Tier?
        false, // Enchantment?
        0, // X Item Level?
        0, // X Quality?
        4, // Watchstone Count?
        false, // Two-Implicit Corrupted?
        true, // Corrupted?
        false, // Unidentified Corrupted?
        "", // Influence?
        "5", // X Stack
        "''Our rulers are being ridiculous, and we are suffering.''", // Description
        "N/A", // Area Drops
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