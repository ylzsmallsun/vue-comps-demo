<template>
  <div class="bar">
    <div  class="inner-bar">
      <div :style="{ width: value + '%', height: barHeight + 'px'}" class="bg-bar">
      </div>
    </div>
    <div >{{ value }}%</div>
  </div>
</template>
<script>
export default {
  name: 'Progress',
  props: {
    value: Number,
    barHeight: {
      type: Number,
      default: 20
    }
  }
}
</script>
<style>
.bar {
  width: 200px;
  height: 20px;
  position: relative;
}
.inner-bar {
  display: inline-block;
  width: 100%;
  background-color: #f3f3f3;
  border-radius: 100px;
  vertical-align: middle;
  position: relative;
}
.bg-bar {
  text-align: right;
  border-radius: 100px;
  background-color: #2d8cf0;
  transition: all .2s linear;
  position: relative;
}
</style>

