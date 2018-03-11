<template>
  <div>
    <table id='board' >
    <tr v-for='(array, i) in board' :key='i'>
        <td v-for='(item, j) in array' :key='j'>
            <span :class='getColorClass(item)' :key='item'></span>
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
    getColorClass(integer) {
      if (integer === -1) {
        return 'disc white';
      } else if (integer === 1) {
        return 'disc black';
      }
      return '';
    },
    setNumber(x, y, num) {
      this.board[y].splice(x, 1, num);
    },
  },
};
</script>


<style scoped>
#board{
text-align: center;
margin-left: auto;
 margin-right: auto;
}
#board > tr > td{
    width: 80px;
    height: 80px;
    border: solid;
    background-color:lawngreen
}
#board > tr > td >span.disc.black{
    display: inline-block;
    width: 80px;
    height: 80px;
    background-color: black;
    border-radius: 75px;
}
#board > tr > td >span.disc.white{
    display: inline-block;
    width: 80px;
    height: 80px;
    background-color: white;
    border-radius: 75px;
}
</style>
