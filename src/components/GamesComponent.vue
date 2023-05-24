<template>
  <div class="games">
    Choose game:
    <el-radio v-for="game in games" :key="game.key" v-model="currentGame" :label="game">{{ game.name}}</el-radio>
    <el-button type="primary" @click="playGame">{{ currentGame.actionName }}</el-button>
    <div v-if="currentItem">{{ currentItem }}</div>
  </div>
</template>

<script>
export default {
  name: 'GamesComponent',
  data() {
    return {
      games: [
        {name: 'flip', actionName: 'Toss a coin', items: ['heads', 'tails']},
        {name: 'dice', actionName: 'Roll the dice', items: ['1', '2', '3', '4', '5', '6']},
        {name: 'cards', actionName: 'Pick card', items: ['6 club', '7 club', '8 club', '9 club', '10 club', 'J club', 'Q club', 'K club', 'Ace club', 
                                                        '6 heart', '7 heart', '8 heart', '9 heart', '10 heart', 'J heart', 'Q heart', 'K heart', 'Ace heart',
                                                        '6 spade', '7 spade', '8 spade', '9 spade', '10 spade', 'J spade', 'Q spade', 'K spade', 'Ace spade',
                                                        '6 diamond', '7 diamond', '8 diamond', '9 diamond', '10 diamond', 'J diamond', 'Q diamond', 'K diamond', 'Ace diamond']}
      ],
      currentGame: {},
      currentItem: ''
    }
  },
  methods: {
    playGame() {
      let randomNumber = Math.random() * (this.currentGame.items.length);
      let randomNumberInteger = Math.floor(randomNumber);
      let item = this.currentGame.items[randomNumberInteger];

      this.currentItem = item;
    }

  },
  mounted() {
    this.currentGame = this.games[0];
  }
}
</script>
