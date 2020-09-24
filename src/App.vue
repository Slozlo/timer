<template>
  <div id="app">
    <timer v-for="item in timers" :key="item" />
    <div>
      <add-timer :add="addTimer" />
    </div>
  </div>
</template>

<script>
import Timer from './components/Timer/Timer';
import AddTimer from './components/AddTimer/AddTimer';

export default {
  name: 'App',
  components: {
    Timer,
    AddTimer
  },
  data() {
    return {
      timers: [1]
    };
  },
  methods: {
    addTimer() {
      const timersCount = this.timers.length;
      const lastItem = this.timers[timersCount - 1];
      const newItem = lastItem + 1;
      const newArr = [...this.timers, newItem];
      this.timers = newArr;
    }
  }
};
</script>

<style>
@font-face {
  font-family: Gotham Pro;
  src: url(./assets/fonts/GothamPro-Light.ttf);
}
#app {
  margin-top: 60px;
  display: flex;
  flex-wrap: wrap;
  justify-content: start;
  font-family: 'Gotham Pro';
}

.right {
  transform: translate3d(10px, 0px, 0px);
}
</style>
