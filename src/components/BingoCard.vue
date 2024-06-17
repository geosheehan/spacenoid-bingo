<!-- src/components/BingoCard.vue -->
<template>
    <div class="bingo-card">
      <h1 class="card-title">Spacenoid Bingo</h1>
      <div v-for="rowIndex in 4" :key="rowIndex" class="bingo-row">
        <div
          v-for="colIndex in 4"
          :key="colIndex"
          class="bingo-cell"
          :class="{ marked: card[(rowIndex - 1) * 4 + (colIndex - 1)].marked }"
          @click="toggleCell((rowIndex - 1) * 4 + (colIndex - 1))"
        >
          {{ card[(rowIndex - 1) * 4 + (colIndex - 1)].value }}
        </div>
      </div>
      <div class="rewards">
        <h2 class="rewards-header">Rewards</h2>
        <ul class="rewards-list">
          <li>• Discord Flair</li>
          <li>• Colored Sketch</li>
          <li>• 1000 Streamlabs Peanuts</li>
        </ul>
      </div>
      <span>• one bingo card per viewer per stream •</span>
      <p class="twitch">
        <a href="https://www.twitch.tv/suavespacenoid">twitch.tv/suavespacenoid</a>
      </p>
    </div>
  </template>
  
  <script>
  export default {
    name: 'BingoCard',
    data() {
      return {
        card: this.generateBingoCard()
      };
    },
    methods: {
      generateBingoCard() {
        const values = [
          "broken alerts",
          "\"can i say that on stream?\"",
          "distracted by chat",
          "#27",
          "sight seeing",
          "energy drink ASMR",
          ".png glitch",
          "assistant \"assists\"",
          "spicy co-pilot",
          "jump scared",
          "* suave noises intensify *",
          "looks up a word",
          "suave words no good",
          "stream snackies",
          "suave sings",
          "someone catches 5 stars"
        ];
        
        // Shuffle the values array
        for (let i = values.length - 1; i > 0; i--) {
          const j = Math.floor(Math.random() * (i + 1));
          [values[i], values[j]] = [values[j], values[i]];
        }
  
        // Create the card array with shuffled values
        return values.map(value => ({ value, marked: false }));
      },
      toggleCell(index) {
        this.card[index].marked = !this.card[index].marked;
      }
    }
  };
  </script>
  
  <style scoped>
  .card-title {
    width: 50%;
    margin: auto;
    font-family: 'Lobster', cursive;
  }

  .bingo-card {
    display: grid;
    grid-template-rows: repeat(4, 1fr);
    gap: 10px;
    width: 500px;
    margin: auto;
    background-color: #fcf3e5;
    padding: 20px;
    padding-right: 20px;
    padding-top: 20px;
    border-radius: 10px;
  }
  .bingo-row {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
  }
  .bingo-cell {
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 8%;
    border: 3px solid #223943;
    background-color: #b0bbb4;
    width: 100%;
    padding-bottom: 80%;
    cursor: pointer;
    user-select: none;
    text-align: center;
    padding: 5px;
    font-weight: bold;
    min-height: 96px;
  }
  /* Apply red background to alternate cells in each row */
  .bingo-row:nth-child(odd) .bingo-cell:nth-child(odd),
  .bingo-row:nth-child(even) .bingo-cell:nth-child(even) {
    border: 3px solid #b0bbb4;
    background-color: #eff3f4;
  }
  .bingo-cell.marked {
    background-color: #ccb65d !important;
    border-color: #917c29 !important;
  }
  .rewards {
    display: flex;
    margin-top: 10px;
  }
  .rewards-header {
    width: 50%;
    font-family: 'Lobster', cursive;
    font-size: 58px
  }
  .rewards-list {
    display: flex;
    flex-wrap: wrap;
    flex: 1 1 auto;
    list-style-type: none;
    padding: 0;
    margin: 0;
    font-family: 'Lobster', cursive;
    font-size: 20px;
  }
  .rewards-list li:first-child,
  .rewards-list li:nth-child(2) {
    flex: 1;
    max-width: 50%;
  }
  .rewards-list li:nth-child(3) {
    flex: 1 1 100%;
  }
  .twitch {
    background-color: white;
    border-radius: 100px;
    padding: 10px 40px;
    margin: auto;
    font-weight: bold;
  }
  .twitch a {
    text-decoration: none;
    color: black;
  }
  .twitch a:hover {
    text-decoration: underline;
  }
</style>
  