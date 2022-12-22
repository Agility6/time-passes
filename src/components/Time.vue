<template>
  <div class="container">

    <div class="time-container">
      <div class="hour-container">
        <div class="time-font">{{ hourString }}</div>
      </div>
      <span class="time-font ">:</span>
      <div class="time-container-style">
        <div class="min time-font">{{ minString }}</div>
      </div>
      <div class="time-container-style">
        <div class="time-font">{{ secString }}</div>
      </div>
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
      hourString: '00',
      minString: '59',
      secString: '55',
      hour: 0,
      min: 59,
      sec: 55
    }
  },
  watch: {
    sec() {
      if(this.sec === 62) {
        this.secString = '00'
        this.sec = 0
        this.min++
        this.minChange()
      }
    },
    min() {
      if(this.min === 60) {
        this.minString = '00'
        this.min = 0
        this.hour++
        this.hourChange()
      }
    }
  },
  methods: {
    startTime() {
      clearInterval(this.timeIntervId)
      this.timeIntervId = setInterval(() => {
        console.log(this.sec);
        this.secString = this.sec < 10 ? `0${this.sec++}` : `${this.sec++}`
      }, 1000)
    },
    stopTime() {
      clearInterval(this.timeIntervId)
    },
    minChange() {
      this.minString = this.min < 10 ? `0${this.min}` : this.min 
    },
    hourChange() {
      this.hourString = this.hour < 10 ? `0${this.hour}` : this.hour
    }
  },
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
    width: 1000px;
    height: 230px;
    justify-content: center;
    // background-color: #A69580;      
    .hour-container {
      display: flex;
      justify-content: center;
      align-items: center;
      margin-right: 50px;
    }
    .time-container-style {
      display: flex;
      justify-content: center;
      align-items: center;
      .min {
        margin: 0 50px;
      }
    }
    .time-font {
      font-size: 180px;
      font-weight: 900;
    }
    span {
      line-height: 200px;
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
