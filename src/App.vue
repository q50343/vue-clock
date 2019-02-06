<template>
  <div id="app">
    <div class="outer">
      <div class="clock">
        <div class="part" v-for='x in 12' :key='x' :style='`transform: rotate(${x*30-30}deg)`'>
          <div class="dot1">
            <div class="dot"></div>
          </div>
          <div class="dot2">
            <div class="dot"></div>
          </div>
          <div class="diamond-outer">
            <div class="diamond">
              <div class="circle-hide circle-hide1"></div>
              <div class="circle-hide circle-hide2"></div>
              <div class="circle-hide circle-hide3"></div>
              <div class="circle-hide circle-hide4"></div>
            </div>
          </div>
          <div class="dot3">
            <div class="dot"></div>
          </div>
          <div class="dot4">
            <div class="dot"></div>
          </div>
          <div  class='nums'>
            <span :style='`transform: rotate(${-x*30}deg) translateX(-4px)`'>{{x+ 12}}</span>
            <div class="line"></div>
            <span :style='`transform: rotate(${-x*30}deg) translateX(-4px)`' class='num2'>{{x}}</span>
          </div>         
        </div>
        <!-- 指針 -->
        <div class="second" :style='`transform:rotate(${second}deg)`'>
          <div class="second1"></div>
          <div class="second2"></div>
          <div class="second3"></div>
          <div class="second4"></div>
          <div class="second5"></div>
          <div class="second6"></div>
        </div>

        <div class="hour" :style='`transform:translateY(-28px) rotate(${hour}deg)`'></div>
        
        <div class="minute" :style='`transform:translateY(-40px) rotate(${minute}deg)`'>
          <div class="minute-inner"></div>
        </div>
        
      </div>
    </div>
   </div> 
</template>

<script>


export default {
  data(){
    return{
      hour: new Date().getHours()*30,
      minute: new Date().getMinutes()*6,
      second: new Date().getSeconds()*6
    }
  },
  created(){ 
    setInterval(()=>{
      let time = new Date()
      this.hour = time.getHours()*30
      this.minute = time.getMinutes()*6
      this.second = time.getSeconds()*6
    },1000)
  }
}
</script>

<style>
html,body{
  background: #293B29;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 95%;
}
.outer{
  background: #3d5a45;
  border-radius: 50px;
  width: 350px;
  height: 350px;
  display: flex;
  justify-content: center;
  align-items: center;
  box-shadow: 0 0 50px rgba(0, 0, 0, .1)
}
.clock{
  width: 300px;
  height: 300px;
  border-radius: 50%;
  background: #293B29;
  border: 5px solid #212f0b;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
}
.part{
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
}
.diamond-outer{
  transform: rotate(15deg)
}
.diamond{
  width: 5px;
  height: 5px;
  background: #ff7600;
  position: absolute;
  top: -122px;
}
.circle-hide{
  width: 5px;
  height: 5px;
  background: #293B29;
  position: absolute;
}
.circle-hide1{
  top: -2px;
  left: -2px;
  border-bottom-right-radius: 100%
}
.circle-hide2{
  top: 2px;
  left: -2px;
  border-top-right-radius: 100%;
}
.circle-hide3{
  top: -2px;
  left: 2px;
  border-bottom-left-radius: 100%;
}
.circle-hide4{
  top: 2px;
  left: 2px;
  border-top-left-radius: 100%;
}
.dot{
  background: #fff;
  width: 2px;
  height: 2px;
  border-radius: 50%;
  position: absolute;
  top: -120px;
}
.dot1{ 
  transform: rotate(5deg)
}
.dot2{
  transform: rotate(10deg)
}
.dot3{
  transform: rotate(20deg)
}
.dot4{
  transform: rotate(25deg)
}
.nums{
  position: absolute;
  transform: rotate(30deg)
}
.line{
  background: #ff7600;
  width: 1px;
  height: 20px;
  position: absolute;
  top: -128px;
  left: -0.5px;
}
span{
  font-size: 8px;
  width:1px;
  color: #fff;
  display: inline-block;
  font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  position: absolute;
  top: -145px;
  transform: translateX(-4px);
  text-align: center;
}
.num2{
  top: -105px;
}
.hour{
  width: 8px;
  height: 62px;
  transform-origin:4px calc(100% - 2px);
  background: #fff;
  position: absolute;
  border-bottom-left-radius: 4px;
  border-bottom-right-radius: 4px;
}
.hour:after{
  content: '';
  width: 2px;
  height: 20px;
  transform: translate(3px,3px);
  background: black;
  position: absolute;
}
.minute{
  width: 8px;
  height: 90px;
  background: #ff7600;
  position: absolute;
  border-radius: 4px;
  transform-origin:4px calc(100% - 4px);  
}
.minute-inner{
  width: 1px;
  height: 25px;
  background: #fff;
  position: absolute;
  bottom:5px;
  transform: translateX(3.5px)
}
.minute-inner:after{
  content: '';
  width: 4px;
  height: 4px;
  background: #fff;
  position: absolute;
  bottom:-3px;
  transform: translateX(-1.4px);
  border-radius: 50%
}
.second1{
  width: 1px;
  height: 40px;
  background: #b1ff00;
  position: absolute;
  transform: translateY(-40px)
}
.second2{
  width: 1px;
  height: 9px;
  background: #b1ff00;
  position: absolute;
  transform: rotate(137deg) translate(-30px,37px);
}
.second3{
  width: 1px;
  height: 23px;
  background: #b1ff00;
  position: absolute;
  transform: rotate(32deg) translate(-36px,-57px);
}
.second4{
  width: 1px;
  height: 9px;
  background: #b1ff00;
  position: absolute;
  transform: rotate(137deg) translate(-51.5px,52px);
}
.second5{
  width: 1px;
  height: 45px;
  background: #b1ff00;
  position: absolute;
  transform:translate(-0.5px,-116px);
}
.second6{
  width: 6px;
  height: 6px;
  border:1px solid #b1ff00;
  border-radius: 50%;
  position: absolute;
  transform:translate(-50%,-123px);
}
.second6:after{
  content: '';
  width: 4px;
  height: 4px;
  background: #b1ff00;
  border-radius: 50%;
  position: absolute;
  transform:translate(1.2px,0.8px);
}
</style>
