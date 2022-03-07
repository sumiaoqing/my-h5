<template>
  <div class="hello">
    <div class="list-show">
      <div class="list-show-item" draggable="able" @dragstart="dragStart(index)" @dragover="dragOver(index)" @dragend="dragEnd(index)" v-for="(item,index) in test_lst" :key="index">
        {{item}}
      </div>
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
export default {
  name: 'HelloWorld',
  data() {
    return {
      checkedStatus: null,
      test_lst: ['test1', 'test2', 'test3', 'test4', 'test5', 'test6'],
      move_id: 'test1'
    };
  },
  methods:
  {
    select(e) {
      console.log(e.target.checked, '0000');
    },
    dragStart(index) {
      this.move_id = index;
      console.log(index);
    },
    dragOver(index) {
      if (index == this.move_id) return
      let temp = this.test_lst[this.move_id];
      Vue.set(this.test_lst, this.move_id, this.test_lst[index]);
      Vue.set(this.test_lst, index, temp);
      console.log(index);

    },
    dragEnd() {

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.list-show {
  width: 200px;
  background: #cdcdcd;
  height: auto;
  position: relative;
  display: flex;
  flex-direction: column;
}
.list-show-item {
  height: 40px;
  background: #345689;
  width: 100%;
  color: #fff;
  border: 1px solid #fff;
  box-sizing: border-box;
}
</style>
