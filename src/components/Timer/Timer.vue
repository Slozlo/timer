<template>
  <div :class="{ [$style.timer]: true, [$style.pause]: isPause }">
    <div :class="{ [$style.time]: true, [$style['time-pause']]: isPause }">
      {{ formattedTime }}
    </div>
    <div :class="$style.icons">
      <div :class="$style.icon">
        <img
          @click="pause"
          v-if="isPause"
          src="../../assets/images/active-pause.svg"
          alt=""
        />
        <img @click="play" v-else src="../../assets/images/play.svg" alt="" />
      </div>
      <div @click="stop" :class="$style.icon">
        <img v-if="isPause" src="../../assets/images/active-stop.svg" alt="" />
        <img v-else src="../../assets/images/stop.svg" alt="" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Timer',
  data() {
    return {
      time: 0,
      timer: null,
      isPause: false
    };
  },
  computed: {
    formattedTime() {
      return this.getTimeFromSeconds(this.time);
    }
  },
  methods: {
    play() {
      this.isPause = !this.isPause;
      this.timer = setInterval(() => {
        this.time += 1;
      }, 1000);
    },
    pause() {
      this.isPause = !this.isPause;
      clearInterval(this.timer);
    },
    stop() {
      this.isPause = false;
      clearInterval(this.timer);
      this.time = 0;
    },
    getTimeFromSeconds(sec) {
      var sec_num = parseInt(sec, 10);
      var hours = Math.floor(sec_num / 3600);
      var minutes = Math.floor((sec_num - hours * 3600) / 60);
      var seconds = sec_num - hours * 3600 - minutes * 60;

      if (hours < 10) {
        hours = '0' + hours;
      }
      if (minutes < 10) {
        minutes = '0' + minutes;
      }
      if (seconds < 10) {
        seconds = '0' + seconds;
      }

      var hoursString = hours > 0 ? hours + ':' : '';
      var minutesString = hours > 0 || minutes > 0 ? minutes + ':' : '';

      return hoursString + minutesString + seconds;
    }
  }
};
</script>

<style module lang="scss">
.timer {
  width: 225px;
  height: 120px;
  background: #696969;
  color: #9e9e9e;
  margin: 45px 50px;
}

.time {
  padding: 20px 70px;
  border-bottom: 1px solid #9e9e9e;
  text-align: center;
}

.icons {
  padding: 20px 70px;
  display: flex;
  justify-content: space-between;
}

.icon {
  &:hover {
    cursor: pointer;
  }
}

.pause {
  color: #ffffff;
}

.time-pause {
  border-bottom: 1px solid #fff;
}
</style>
