<template>
  <div class="wrapper">
    <Progress :value="percentage"/>
    <input class="startBtn" type="button" value="Start" @click="luanchLoading"/>
  </div>
</template>
<script>
import Progress from '../components/Progress.vue'
export default {
  name: 'ProgressDemo',
  components: {
    Progress
  },
  data () {
    return {
      percentage: 0,
      barHeight: 20,
      upLoading: false,
      timer: null
    }
  },
  watch: {
    percentage (val) {
      if (val >= 100) {
        this.upLoading = false
        clearTimeout(this.timer)
      }
    }
  },
  mounted () {
  //  this.luanchLoading()
  },
  methods: {
    luanchLoading () {
      if (this.percentage > 0) {
        this.percentage = 0
      }
      if (!this.upLoading) {
        this.upLoading = true
        this.timer = setInterval(() => {
          this.percentage ++
        },100)
      }
    }
  }
}
</script>
<style>
.wrapper {
  display: flex;
  padding: 20px;
  justify-content: center;
}
.startBtn {
  width: 50px;
  padding: 10px;
  margin-left: 10px;
  font-size: 20px;
}
</style>
