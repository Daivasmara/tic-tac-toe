<template>
  <div id="app">
    <div class="container">
      <div class="tictactoe">
        <div class="row">
          <h1 class="center teal-text">Tic-Tac-Toe</h1>
        </div>
        <div class="gamearea row center-align teal-text">
          <div @click="changeTurn(1)" class="col grid s4 m2 offset-m3"><i class="material-icons">{{ area1 }}</i></div>
          <div @click="changeTurn(2)" class="col grid s4 m2"><i class="material-icons">{{ area2 }}</i></div>
          <div @click="changeTurn(3)" class="col grid s4 m2"><i class="material-icons">{{ area3 }}</i></div>
          <div @click="changeTurn(4)" class="col grid s4 m2 offset-m3"><i class="material-icons">{{ area4 }}</i></div>
          <div @click="changeTurn(5)" class="col grid s4 m2"><i class="material-icons">{{ area5 }}</i></div>
          <div @click="changeTurn(6)" class="col grid s4 m2"><i class="material-icons">{{ area6 }}</i></div>
          <div @click="changeTurn(7)" class="col grid s4 m2 offset-m3"><i class="material-icons">{{ area7 }}</i></div>
          <div @click="changeTurn(8)" class="col grid s4 m2"><i class="material-icons">{{ area8 }}</i></div>
          <div @click="changeTurn(9)" class="col grid s4 m2"><i class="material-icons">{{ area9 }}</i></div>
        </div>
        <div class="row">
          <a class="waves-effect waves-light btn col s6 m3 offset-m3" :class="{ disabled : !player1Turn }"><i class="material-icons right">panorama_fish_eye</i>PLAYER 1</a>
          <a class="waves-effect waves-light btn col s6 m3" :class="{ disabled : player1Turn }"><i class="material-icons right">clear</i>PLAYER 2</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: "app",
  data() {
    return {
      player1Turn: true,
      symbol: 'panorama_fish_eye',
      area1: '1',
      area2: '2',
      area3: '3',
      area4: '4',
      area5: '5',
      area6: '6',
      area7: '7',
      area8: '8',
      area9: '9',
    }
  },
  methods: {
    changeTurn(number) {
      number === 1 ? this.area1 = this.symbol :
      number === 2 ? this.area2 = this.symbol :
      number === 3 ? this.area3 = this.symbol :
      number === 4 ? this.area4 = this.symbol :
      number === 5 ? this.area5 = this.symbol :
      number === 6 ? this.area6 = this.symbol :
      number === 7 ? this.area7 = this.symbol :
      number === 8 ? this.area8 = this.symbol :
      number === 9 ? this.area9 = this.symbol :
      void(0),
      this.player1Turn = !this.player1Turn
    }
  },
  watch: {
    player1Turn() {
      if(this.player1Turn) {
        this.symbol = 'panorama_fish_eye'
      } else {
        this.symbol = 'clear'
    }
  }
}
};
</script>

<style lang="scss">
  .tictactoe{
    margin-top: 80px;
    .gamearea{
      .grid{
        height: 100px;
        border: 1px solid #26a69a;
        cursor: pointer;
        i{
          margin-top: 35px;
        }
      }
    }
  }
</style>
