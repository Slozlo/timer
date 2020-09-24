<template>
  <div @click="add" :class="$style['add-timer']">
    +
  </div>
</template>

<script>
export default {
  name: 'AddTimer',
  props: {
    add: Function
  }
};
</script>

<style module lang="scss">
.add-timer {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 225px;
  height: 120px;
  background: #696969;
  font-size: 40px;
  color: #9e9e9e;
  margin: 45px 50px;

  &:hover {
    cursor: pointer;
  }
}
</style>
