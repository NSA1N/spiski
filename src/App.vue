<template>
  <div class="section">
    <ol class="table" multiple>
      <li v-for="(item, index) in itemListLeft"
      :class="{selectedLi:  item.selected }"
      @click="doSelected(item)"
      :key="index"
       >
        {{ item.text }}
      </li>
    </ol>
    <div class="images">
      <img
      @click="runObjLeft(itemListLeft, itemListRight)"
      src="../public/arrow.png" alt="">
      <img
      @click="runObjRight(itemListLeft, itemListRight)"
      class="img2" src="../public/arrow.png" alt="">
    </div>
    <ol class="tableTwo">
      <li v-for="(itemRight, index) in itemListRight"
      :class="{selectedLi: itemRight.selected}"
      @click="doSelected(itemRight)"
      :key="index"
      >
        {{ itemRight.text }}
      </li> 
    </ol>
  </div>
</template>

<script>

  export default {
    data () {
      return {
        itemListLeft: [
          {text: 'групша', id: 0, selected: false},
          {text: 'еблоко', id: 1, selected: false},
          {text: 'монго', id: 2, selected: false},
          {text: 'албузик', id: 3, selected: false},
          {text: 'карбюратор', id: 4, selected: false},
        ],
         itemListRight: [
         
         ],
      }
    },
    methods: {
      doSelected (item) {
        item.selected = !item.selected;
      }, 
      runObjRight(itemListLeft, itemListRight) {
        let selectedItems = itemListLeft.filter((item) => item.selected === true);
        this.itemListLeft = itemListLeft.filter((item) => item.selected === false);
        this.itemListRight = [...itemListRight, ...selectedItems];
        for(let item of itemListLeft) {
          item.selected = false;
        }
        for(let item of itemListRight) {
          item.selected = false;
        }
          },

      runObjLeft(itemListLeft, itemListRight) {
        let selectedItems = itemListRight.filter((item) => item.selected === true);
        this.itemListRight = itemListRight.filter((item) => item.selected === false);
        this.itemListLeft = [...itemListLeft, ...selectedItems]
        for(let item of itemListLeft) {
          item.selected = false
        }
        for(let item of itemListRight) {
          item.selected = false;
        }    
      },

      deleteObj(itemList, index) {
        itemList.splice(index, 1)
      },

      pushObj(itemList, obj) {
        itemList.push(obj)
      },
    }}



</script>

<style>
  .section {
    display: flex;
    justify-content: center;
    align-items: center;
    
  }
  .table {
    display:flex;
    border: 1px solid gray;
    flex-direction: column;
    justify-content: flex-start;
    padding: 30px;
    min-width: 400px;
    min-height: 400px;
    background: rgb(165,69,205);
    background: radial-gradient(circle, rgba(165,69,205,1) 0%, rgba(211,233,148,1) 100%);
  }
  .tableTwo {
    display:flex;
    border: 1px solid gray;
    flex-direction: column;
    justify-content: flex-start;
    padding: 30px;
    min-width: 400px;
    min-height: 400px;
    background: rgb(180,58,79);
    background: linear-gradient(90deg, rgba(180,58,79,0.9445028011204482) 0%, rgba(29,253,235,1) 50%, rgba(252,176,69,1) 100%);
  }
  li{
    list-style-type: none;
    margin: 20px;
    
  }
  li:hover{
    cursor: pointer;
  }
  .selectedLi{
    background-color: rgb(0, 166, 255);
    border-radius: 0.5;
    width: 100px;
    color: rgb(200, 255, 0);
  }
  img{
    width: 25px;
    height: 25px;
    margin: 20px;
  }
  img:hover {
    cursor: pointer;
  }
  .img2{
    rotate: 180deg;
  }
  .images {
    display: flex;
  }
</style>
