<template>
  <div>
    <div class="wrapper">
      <Progress :value="percentage"/>
      <input class="startBtn" type="button" value="Start" @click="luanchLoading"/>
    </div>
    <div class="btn" @click="showToast">点击出弹窗提示</div>
    <Toast ref="toast" :message="toastMsg" :time="duration"/>
  </div>
</template>
<script>
import Progress from '../components/Progress.vue'
import Toast from '../components/Toast.vue'
export default {
  name: 'CompsDemo',
  components: {
    Progress,
    Toast
  },
  data () {
    return {
      percentage: 0,
      barHeight: 20,
      upLoading: false,
      timer: null,
      duration: 2000,
      isShowToast: false,
      toastMsg: '操作成功'
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
    },
    showToast () {
      this.$refs['toast'].show()
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
.btn {
  width: 120px;
  background: blue;
  color: #ffffff;
  margin: 10px auto;
}
</style>
