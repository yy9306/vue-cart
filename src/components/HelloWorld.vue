<template>
 <div class="box">
   <ul>
     <li v-for="message in messages" class="message">
       <span class="text">{{message.info}}</span>
       <span class="btn" @click="selectCount">{{message.id}}</span>
     </li>
   </ul>
   <div class="footer-tab">
     <div class="cart-wrapper">

     </div>
   </div>
 </div>
</template>

<script type="text/javascript">
export default {
  data () {
    return {
      messages: [
        {info: 'sfsfsd1', id: 1},
        {info: 'sfsfsd2', id: 1},
        {info: 'sfsfsd3', id: 1},
        {info: 'sfsfsd4', id: 1},
        {info: 'sfsfsd5', id: 1}
      ]
    }
  },
  methods: {
    selectCount () {
      this.$emit('cartAdd', event.target)
    }
  }
}
</script>

<style scoped>
.box{
  width: 100%;
  position: absolute;
  top: 0;
  left: 0;
  bottom: 70px;
}
.box ul{
  width: 100%;
  padding: 0 18px;
  box-sizing: border-box;
}
.message{
  display: flex;
  align-items: center;
  position: relative;
  height: 60px;
  border-bottom: 1px solid #ddd;
}
.btn{
  position: absolute;
  right: 5px;
  top: 20px;
  width: 20px;
  height: 20px;
  background: blue;
  border-radius: 50%;
  color: #fff;
  text-align: center;
}
.footer-tab{
 position: fixed;
 bottom: 0;
 left: 0;
 height: 70px;
 border-top: 1px solid #ddd;
}

</style>
