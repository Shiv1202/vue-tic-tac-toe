<template>
  <h1>Hello world</h1>
</template>

<script>
import Icon from './components/grid.vue'

export default ({
  name: 'App',
  components: { Icon },
  data () {
    return {
      winMessage: "",
      isCross: true,
      itemArray: new Array(9).fill("empty")
    }
  },
  watch: {
    winMessage: function (message){
      if (message) {
        this.showDialog();
      }
    }
  },

  methods: {
    showDialog() {
      document.alert(this.winMessage)
    },
    handleClick (itemNumber){
      if(this.winMessage) {
        return this.showDialog()
      }

      if(this.itemArray[itemNumber] === 'empty') {
        this.itemArray[itemNumber] = this.isCross ? "cross" : "circle"
        this.isCross = !this.isCross
      }else{
        document.alert("Already Filled!")
      }

      this.checkWinner()
    },
    checkWinner(){
      //  checking  winner of the game
      if (
        this.itemArray[0] === this.itemArray[1] &&
        this.itemArray[0] === this.itemArray[2] &&
        this.itemArray[0] !== "empty"
      ) {
        this.winMessage = `${this.itemArray[0]} won`;
      } else if (
        this.itemArray[3] !== "empty" &&
        this.itemArray[3] === this.itemArray[4] &&
        this.itemArray[4] === this.itemArray[5]
      ) {
        this.winMessage = `${this.itemArray[3]} won`;
      } else if (
        this.itemArray[6] !== "empty" &&
        this.itemArray[6] === this.itemArray[7] &&
        this.itemArray[7] === this.itemArray[8]
      ) {
        this.winMessage = `${this.itemArray[6]} won`;
      } else if (
        this.itemArray[0] !== "empty" &&
        this.itemArray[0] === this.itemArray[3] &&
        this.itemArray[3] === this.itemArray[6]
      ) {
        this.winMessage = `${this.itemArray[0]} won`;
      } else if (
        this.itemArray[1] !== "empty" &&
        this.itemArray[1] === this.itemArray[4] &&
        this.itemArray[4] === this.itemArray[7]
      ) {
        this.winMessage = `${this.itemArray[1]} won`;
      } else if (
        this.itemArray[2] !== "empty" &&
        this.itemArray[2] === this.itemArray[5] &&
        this.itemArray[5] === this.itemArray[8]
      ) {
        this.winMessage = `${this.itemArray[2]} won`;
      } else if (
        this.itemArray[0] !== "empty" &&
        this.itemArray[0] === this.itemArray[4] &&
        this.itemArray[4] === this.itemArray[8]
      ) {
        this.winMessage = `${this.itemArray[0]} won`;
      } else if (
        this.itemArray[2] !== "empty" &&
        this.itemArray[2] === this.itemArray[4] &&
        this.itemArray[4] === this.itemArray[6]
      ) {
        this.winMessage = `${this.itemArray[2]} won`;
      }
    },
    reloadGame(){
      this.winMessage = "";
      this.isCross = true;
      this.itemArray = new Array(9).fill("empty")
    }
  }
})
</script>

<style>

</style>
