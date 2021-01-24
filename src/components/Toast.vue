<template>
  <div v-if="isShow" :class="position" class="toast">
    <span class="toast-text">{{ message }}</span>
  </div>  
</template>
<script>
export default {
  name: 'Toast',
  props: {
    message: String,
    time: {
      type: Number,
      default: 1000
    },
    position: {
      type: String,
      default: 'middle'
    }
  },
  data () {
    return {
      isShow: false
    }
  },
  mounted () {
  },
  watch: {
    isShow (val) {
      if(val) {
        setTimeout(() => {
          this.hide()
        }, this.time)
      }
    }
  },
  methods: {
    hide () {
      this.isShow = false
    },
    show () {
      this.isShow = true
    }
  }
}
</script>
<style>
.toast {
    position: fixed;
    max-width: 80%;
    border-radius: 5px;
    background: rgba(0,0,0,.7);
    color: #fff;
    box-sizing: border-box;
    text-align: center;
    z-index: 1000;
    -webkit-transition: opacity .3s linear;
    transition: opacity .3s linear;
    padding: 10px;
}
.toast.middle {
  left: 50%;
  top: 50%;
  -webkit-transform: translate(-50%,-50%);
  transform: translate(-50%,-50%);
}
</style>
