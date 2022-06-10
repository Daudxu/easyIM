<template>
  <div class="home" @mousemove="getMouseXY($event)">
        <button @click="ceshi">test</button>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Test',
  sockets: {
    connect: function () {

      console.log('socket to notification channel connected')
    },
    sa: function (data) {
      console.log(data)
    },

  },

  data () {
    return {
      x:0,
      y:0,
    }
  },
  methods: {
      ceshi(){
         this.$socket.emit('message', 123123)
        //  console.log(this.$socket)
      },
      getMouseXY(e){
        this.x = e.pageX 
        this.y = e.pageY 
         this.$socket.emit('message', {
              x:e.pageX,
              y:e.pageY,
         })
    },
  },
}
</script>
<style lang="stylus" scoped>
div {
  width: 100%;
  height: 100vh;
  background: #000
}
</style>
