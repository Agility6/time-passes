<template>
  <div class="container">

    <div class="time-container">
      <div class="time-string-font">{{ timeString }}</div>
    </div>

    <div class="btn-container">
      <button @click="startTime" class="start btn-font">Start</button>
      <button @click="stopTime" class="stop btn-font">Stop</button>
    </div>

  </div>
</template>

<script>
export default {
  name: 'Time',
  data() {
    return {
      timeString: "00:00:00",
      hour: 0,
      min: 0,
      sec: 0
    }
  },
  methods: {
    startTime() {
      // 重复点击
      if(this.timer) clearInterval(this.timer)

      this.timer = setInterval(() => {
        this.sec += 1;
        if(this.sec >= 60) {
          this.sec = 0;
          this.min = this.min + 1;
        }
        if(this.min >= 60) {
          this.min = 0;
          this.hour = this.hour + 1;
        }
        this.timeString = `${this.toFull(this.hour)}:${this.toFull(this.min)}:${this.toFull(this.sec)}`
      }, 1000)
    },
    stopTime() {
      clearInterval(this.timer)
    },
    toFull(time) {
      return time < 10? "0"+time : time
    }
  }
}
</script>

<style lang="scss">
 .container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
  .time-container {
   display: flex;
   justify-content: center;
   align-items: center;
   height: 200px;
   .time-string-font {
    font-size: 150px;
    font-weight: 900;
   }
  }
  .btn-container {
    display: flex;
    width: 1000px;
    height: 100px;
    justify-content: center;
    .start {
      width: 200px;
      margin-right: 50px;
    }
    .stop {
      width: 200px;
    }
    .btn-font {
      font-size: 35px;
      font-weight: 900;
      background-color: #023059;
      border: 1px solid transparent;
      color: #91BBF2;
      border-radius: 15px;
      &:hover {
        background-color: #0367A6;
      }
    }
  }
 }
</style>
