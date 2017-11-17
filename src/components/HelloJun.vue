<template>
   <div class="footer-tab">
     <div class="cart-wrapper">
       车
     </div>
     <div class="ball-container">
       <transition-group name="drop" @before-enter="beforeDrop" @enter="dropping" @after-enter="afterDrop">
         <div class="ball" v-for="(ball, index) in balls" v-show="ball.show" :key="index">
           <div class="inner inner-hook">1</div>
         </div>
       </transition-group>
     </div>
   </div>
</template>

<script type="text/javascript">
export default {
  data () {
    return {
      balls: [
        {
          show: false
        },
        {
          show: false
        },
        {
          show: false
        },
        {
          show: false
        },
        {
          show: false
        }
      ],
      dropBalls: []
    }
  },
  methods: {
    drop (el) {
      for (let i = 0; i < this.balls.length; i++) {
        let ball = this.balls[i]
        if (!ball.show) {
          ball.show = true
          ball.el = el
          this.dropBalls.push(ball)
          return
        }
      }
    },
    beforeDrop (el) {
      let count = this.balls.length
      while (count--) {
        let ball = this.balls[count]
        if (ball.show) {
          let rect = ball.el.getBoundingClientRect()
          let x = rect.left - 25
          let y = -(window.innerHeight - rect.top - 25)
          el.style.display = ''
          el.style.webkitTransform = `translate3d(0, ${y}px, 0)`
          el.style.transform = `translate3d(0, ${y}px, 0)`
          let inner = el.getElementsByClassName('inner-hook')[0]
          inner.style.webkitTransform = `translate3d(${x}px, 0, 0)`
          inner.style.transform = `translate3d(${x}px, 0, 0)`
        }
      }
    },
    dropping (el, done) {
      /* eslint-disable no-unused-vars */
      let rf = el.offsetHeight
      el.style.webkitTransform = 'translate3d(0, 0, 0)'
      el.style.transform = 'translate3d(0, 0, 0)'
      let inner = el.getElementsByClassName('inner-hook')[0]
      inner.style.webkitTransform = 'translate3d(0, 0, 0)'
      inner.style.transform = 'translate3d(0, 0, 0)'
      el.addEventListener('transitionend', done)
    },
    afterDrop (el) {
      let ball = this.dropBalls.shift()
      if (ball) {
        ball.show = false
        el.style.display = 'none'
      }
    }
  }
}
</script>

<style scoped>
.footer-tab{
 position: fixed;
 bottom: 0;
 left: 0;
 width: 100%;
 height: 70px;
 background: #fff;
 border-top: 1px solid #ddd;
}
.cart-wrapper{
  margin: 20px 0 0 20px;
  width: 30px;
  height: 30px;
  background: red;
  color: #fff;
  text-align: center;
  line-height: 30px;
}
.ball{
  position: fixed;
  left: 25px;
  bottom: 25px;
  z-index: 200;
  text-align: center;
  color: #fff;
}
.ball.drop-enter-active{
  transition: all 0.4s cubic-bezier(0.49, -0.29, 0.75, 0.41);
}
.ball.drop-enter-active .inner{
  transition: all 0.4s linear;
}
.ball .inner{
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: rgb(0, 160, 220);
}

</style>
