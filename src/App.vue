<template>
  <div id="app">
    <div class="container">
      <div class="tictactoe">
        <div class="row">
          <h1 class="center teal-text">Tic-Tac-Toe</h1>
        </div>
        <div class="gamearea row center-align teal-text">
          <div @click="changeTurn(1)" class="col grid s4 m2 offset-m3"><i class="large material-icons">{{ area1 }}</i></div>
          <div @click="changeTurn(2)" class="col grid s4 m2"><i class="large material-icons">{{ area2 }}</i></div>
          <div @click="changeTurn(3)" class="col grid s4 m2"><i class="large material-icons">{{ area3 }}</i></div>
          <div @click="changeTurn(4)" class="col grid s4 m2 offset-m3"><i class="large material-icons">{{ area4 }}</i></div>
          <div @click="changeTurn(5)" class="col grid s4 m2"><i class="large material-icons">{{ area5 }}</i></div>
          <div @click="changeTurn(6)" class="col grid s4 m2"><i class="large material-icons">{{ area6 }}</i></div>
          <div @click="changeTurn(7)" class="col grid s4 m2 offset-m3"><i class="large material-icons">{{ area7 }}</i></div>
          <div @click="changeTurn(8)" class="col grid s4 m2"><i class="large material-icons">{{ area8 }}</i></div>
          <div @click="changeTurn(9)" class="col grid s4 m2"><i class="large material-icons">{{ area9 }}</i></div>
        </div>
        <div class="row">
          <a
            class="waves-effect waves-light btn col s6 m3 offset-m3"
            :class="{ disabled : !player1Turn }">
            <i class="material-icons left">panorama_fish_eye</i>
            PLAYER 1
          </a>
          <a
            class="waves-effect waves-light btn col s6 m3"
            :class="{ disabled : player1Turn }">
            <i class="material-icons right">clear</i>
            PLAYER 2
          </a>
          <transition name="bounce">
            <a
              v-if="area1 !== '1' || area2 !== '2' || area3 !== '3' || area4 !== '4' || area5 !== '5' || area6 !== '6' || area7 !== '7' || area8 !== '8' || area9 !== '9' "
              @click="reset"
              class="teal-text col s12 m6 offset-m3 center refresh">
              <i class="medium material-icons">refresh</i>
            </a>
          </transition>
          <transition name="bounce">
            <a v-if="result" class="waves-effect waves-light btn col s12 m6 offset-m3 pulse">
              {{ winner }} VICTORY
            </a>
          </transition>
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
      symbol: "panorama_fish_eye",
      area1: "1",
      area2: "2",
      area3: "3",
      area4: "4",
      area5: "5",
      area6: "6",
      area7: "7",
      area8: "8",
      area9: "9",
      result: false,
      winner: ""
    };
  },
  methods: {
    changeTurn(number) {
      number === 1 && this.area1 == "1"
        ? (this.area1 = this.symbol)
        : number === 2 && this.area2 == "2"
          ? (this.area2 = this.symbol)
          : number === 3 && this.area3 == "3"
            ? (this.area3 = this.symbol)
            : number === 4 && this.area4 == "4"
              ? (this.area4 = this.symbol)
              : number === 5 && this.area5 == "5"
                ? (this.area5 = this.symbol)
                : number === 6 && this.area6 == "6"
                  ? (this.area6 = this.symbol)
                  : number === 7 && this.area7 == "7"
                    ? (this.area7 = this.symbol)
                    : number === 8 && this.area8 == "8"
                      ? (this.area8 = this.symbol)
                      : number === 9 && this.area9 == "9"
                        ? (this.area9 = this.symbol)
                        : (this.player1Turn = !this.player1Turn),
        this.area1 === this.area2 && this.area1 === this.area3
          ? this.area1 === "panorama_fish_eye"
            ? ((this.winner = "Player 1"), (this.result = true))
            : ((this.winner = "Player 2"), (this.result = true))
          : this.area4 === this.area5 && this.area4 === this.area6
            ? this.area4 === "panorama_fish_eye"
              ? ((this.winner = "Player 1"), (this.result = true))
              : ((this.winner = "Player 2"), (this.result = true))
            : this.area7 === this.area8 && this.area7 === this.area9
              ? this.area7 === "panorama_fish_eye"
                ? ((this.winner = "Player 1"), (this.result = true))
                : ((this.winner = "Player 2"), (this.result = true))
              : this.area1 === this.area4 && this.area1 === this.area7
                ? this.area1 === "panorama_fish_eye"
                  ? ((this.winner = "Player 1"), (this.result = true))
                  : ((this.winner = "Player 2"), (this.result = true))
                : this.area2 === this.area5 && this.area2 === this.area8
                  ? this.area2 === "panorama_fish_eye"
                    ? ((this.winner = "Player 1"), (this.result = true))
                    : ((this.winner = "Player 2"), (this.result = true))
                  : this.area3 === this.area6 && this.area3 === this.area9
                    ? this.area3 === "panorama_fish_eye"
                      ? ((this.winner = "Player 1"), (this.result = true))
                      : ((this.winner = "Player 2"), (this.result = true))
                    : this.area1 === this.area5 && this.area1 === this.area9
                      ? this.area1 === "panorama_fish_eye"
                        ? ((this.winner = "Player 1"), (this.result = true))
                        : ((this.winner = "Player 2"), (this.result = true))
                      : this.area7 === this.area5 && this.area7 === this.area3
                        ? this.area7 === "panorama_fish_eye"
                          ? ((this.winner = "Player 1"), (this.result = true))
                          : ((this.winner = "Player 2"), (this.result = true))
                        : (this.player1Turn = !this.player1Turn);
    },
    reset() {
      (this.area1 = "1"),
        (this.area2 = "2"),
        (this.area3 = "3"),
        (this.area4 = "4"),
        (this.area5 = "5"),
        (this.area6 = "6"),
        (this.area7 = "7"),
        (this.area8 = "8"),
        (this.area9 = "9"),
        (this.player1Turn = true),
        (this.result = false),
        (this.winner = "");
    }
  },
  watch: {
    player1Turn() {
      if (this.player1Turn) {
        this.symbol = "panorama_fish_eye";
      } else {
        this.symbol = "clear";
      }
    }
  }
};
</script>

<style lang="scss">
.tictactoe {
  margin-top: 80px;
  .gamearea {
    .grid {
      height: 100px;
      border: 1px solid #26a69a;
      cursor: pointer;
    }
  }
  .bounce-enter-active {
    animation: bounce-in 0.5s;
  }
  .bounce-leave-active {
    animation: bounce-in 0.5s reverse;
  }
  @keyframes bounce-in {
    0% {
      transform: scale(0);
    }
    50% {
      transform: scale(1.5);
    }
    100% {
      transform: scale(1);
    }
  }
  .refresh {
    cursor: pointer;
    margin-top: 30px;
  }
}
</style>
