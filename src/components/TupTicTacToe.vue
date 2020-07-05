<template>
  <div>
    <div ref="board">
      <p>Get your party off to a flying start by playing</p>
      <h1 class="blue-text">{{board.hostName}}</h1>
      <p>and earning additional rewards!</p>

      <table class="tictactoe">
        <tr>
          <td class="blue">{{board.goal1}}</td>
          <td class="yellow">{{board.goal2}}</td>
          <td class="red">{{board.goal3}}</td>
        </tr>
        <tr>
          <td class="red">{{board.goal4}}</td>
          <td class="green">{{board.goal5}}</td>
          <td class="blue">{{board.goal6}}</td>
        </tr>
        <tr>
          <td class="green">{{board.goal7}}</td>
          <td class="blue">{{board.goal8}}</td>
          <td class="yellow">{{board.goal9}}</td>
        </tr>
      </table>

      <table class="prizes">
        <tr>
          <td>3 Squares</td>
          <td>6 Squares</td>
          <td>All Squares</td>
        </tr>
        <tr class="prize-text">
          <td>
            <h2 class="red-text">{{board.prize1}}</h2>
          </td>
          <td>
            <h2 class="blue-text">{{board.prize2}}</h2>
          </td>
          <td>
            <h2 class="green-text">{{board.prize3}}</h2>
          </td>
        </tr>
      </table>
    </div>

    <hr>Screenshot the above, and crop it to just the above!
    <p>
      <small>
        <em>
          Made by Brett Taylor -
          <a href="https://twitter.com/glutnix">@glutnix on twitter</a>
          if you like it, tell me and a friend!
        </em>
      </small>
    </p>
    <hr>

    <h2>Edit Grid</h2>

    <input v-model="board.hostName">
    <ol>
      <li>
        <input v-model="board.goal1">
      </li>
      <li>
        <input v-model="board.goal2">
      </li>
      <li>
        <input v-model="board.goal3">
      </li>
      <li>
        <input v-model="board.goal4">
      </li>
      <li>
        <input v-model="board.goal5">
      </li>
      <li>
        <input v-model="board.goal6">
      </li>
      <li>
        <input v-model="board.goal7">
      </li>
      <li>
        <input v-model="board.goal8">
      </li>
      <li>
        <input v-model="board.goal9">
      </li>
    </ol>
    <ol>
      <li>
        <input v-model="board.prize1">
      </li>
      <li>
        <input v-model="board.prize2">
      </li>
      <li>
        <input v-model="board.prize3">
      </li>
    </ol>
    <p>What you enter here is saved on your device and will be here when you return.</p>
    <button @click="resetBoard">Reset grid to defaults</button>
  </div>
</template>

<script>
const defaultBoard = {
  hostName: "Name's TicTacToe",
  goal1: "8+ adult Guests in attendance",
  goal2: "$1000 in Party Sales",
  goal3: "Date-in-waiting dd/mm/yyyy",
  goal4: "3+ Guests in attendance that your Consultant has never met",
  goal5: "Hold party on originally scheduled date dd/mm/yyyy",
  goal6: "Special Challenge: $600 minimum sales",
  goal7: "20+ names on your Guest list",
  goal8: "Personally invite everyone on your Guest list",
  goal9: "$300 in orders before your Party",
  prize1: "1 Prize",
  prize2: "2 Prizes",
  prize3: "3 Prizes"
};
export default {
  name: "TupTicTacToe",
  data() {
    return {
      board: { ...defaultBoard }
    };
  },
  watch: {
    board: {
      handler() {
        localStorage.setItem("board", JSON.stringify(this.board));
      },
      deep: true
    }
  },
  mounted() {
    if (localStorage.getItem("board"))
      this.board = JSON.parse(localStorage.getItem("board"));
  },
  methods: {
    resetBoard() {
      if (confirm("Reset? This is not undoable.")) {
        this.board = { ...defaultBoard };
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
* {
  box-sizing: border-box;
}
$blue: #1ab5da;
$yellow: #fed116;
$red: #e01083;
$green: #51b042;
.blue {
  background-color: $blue;
}
.yellow {
  background-color: $yellow;
}
.red {
  background-color: $red;
}
.green {
  background-color: $green;
}
.blue-text {
  color: $blue;
  text-shadow: 0 0 10px $blue;
}
.yellow-text {
  color: $yellow;
  text-shadow: 0 0 10px $yellow;
}
.red-text {
  color: $red;
  text-shadow: 0 0 10px $red;
}
.green-text {
  color: $green;
  text-shadow: 0 0 10px $green;
}
html,
body {
  font-size: 0.7em;
  margin: 0;
  padding: 1px;
}
button {
  width: 100%;
  font-size: 1em;
  padding: 0.5em;
}
.board {
  max-height: 90vh;
}
p {
  margin: 0.5em;
}
h1 {
  margin: 0;
}
h2,
h3 {
  margin: 0.5em;
  padding: 0;
}
table {
  width: 100%;
  max-width: 35em;
  margin: 1em auto;

  td {
    width: 33.33333%;
    vertical-align: center;
    text-align: center;
  }
}
.tictactoe td {
  height: 10em;
  padding: 1em;
  font-weight: bold;
  color: white;
  text-shadow: 0 0 10px #000;
}
.prizes td {
  vertical-align: top;
}
input {
  font-size: 1em;
  width: 100%;
}
</style>

