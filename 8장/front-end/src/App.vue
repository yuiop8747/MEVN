<template>
  <div id="app">
  <div class="flexCenter">
    <circleComponent _key="cpuUsage" _key2="CPU"></circleComponent>
    <circleComponent _key="memUsage" _key2="메모리"></circleComponent> 
  </div>  
  <chart _key="response-time"></chart>  
  <button @click="test" class="testButton">애러테스트</button>  
  </div>
</template>

<script>
  import circleComponent from './components/circle.vue'
  import chart from './components/chart.vue'  

  import { 
    mapActions
  } from 'vuex'
  export default {
    name: 'app',
    components: {
      circleComponent, 
      chart
    }, 
    mounted() {
      this.initLog(this.$socket);
    },
    methods: { 
      ...mapActions([
        'initLog', 'test'
      ])
    }
  }
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Lato&display=swap');  
p{
  margin: 0 auto;
}  
body{
  margin:0 auto; 
  height:100%;
}
#app{ 
  background: #f2f4f7;
  font-family:'Lato';
  text-align:center;
  height: 100%;
  box-sizing: border-box;
}
.flexCenter{
  display: flex;
  align-items: center;
  justify-content: center;
}
.flexCenter div{
  margin: 0 20px;
}
.testButton{
  border:none;
  background: #fff;  
  border: 1px solid #dee3eb; 
  padding: 6px 30px;
  font-family:'Lato';
  font-size:1rem;
  transition:all .5s;
}
.testButton:hover{
  cursor: pointer;
  background: rgba(249, 158, 26, 0.7);
} 
</style>