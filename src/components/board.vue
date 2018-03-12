<template>
  <div>
    <table id='board' >
    <tr v-for='(array, i) in board' :key='i'>
        <td v-for='(item, j) in array' :key='j' v-on:click='onClickCell(j,i)'>
            <span :class='getColorClass(j, i)' :key='item'></span>
        </td>
    </tr>
    </table>
  </div>
</template>
<script>
export default {
  data() {
    return {
      board: [
        [0, 0, 0, 0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0, 0, 0, 0],
      ],
      currentTrunColor: 1,
    };
  },
  mounted() {
    console.log(this.board[0][0]);
    this.setNumber(3, 3, 1);
    this.setNumber(4, 4, 1);
    this.setNumber(3, 4, -1);
    this.setNumber(4, 3, -1);
    console.log(this.board);
  },
  methods: {
    getColorClass(x, y) {
      if (this.getNumber(x, y) === -1) {
        return 'disc white';
      } else if (this.getNumber(x, y) === 1) {
        return 'disc black';
      }
      return '';
    },
    getNumber(x, y) {
      return this.board[y][x];
    },
    setNumber(x, y, num) {
      this.board[y].splice(x, 1, num);
    },
    onClickCell(x, y) {
      console.log('x', x);
      console.log('y', y);
      this.setNumber(x, y, this.currentTrunColor);
      this.currentTrunColor *= -1;
    },
  },
};
</script>


<style scoped>
#board {
  text-align: center;
  margin-left: auto;
  margin-right: auto;
}
#board > tr {
  height: 95px;
}
#board > tr > td {
  width: 80px;
  height: 80px;
  border: solid;
  background-color: lawngreen;
}
#board > tr > td > span.disc.black {
  display: inline-block;
  width: 80px;
  height: 80px;
  background-color: black;
  border-radius: 75px;
  margin-top: 1px;
}
#board > tr > td > span.disc.white {
  display: inline-block;
  width: 80px;
  height: 80px;
  background-color: white;
  border-radius: 75px;
  margin-top: 1px;
}
</style>
