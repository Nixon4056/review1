<template>
  <div class="wrapper">
    <the-modal></the-modal>
  </div>
</template>

<script>
import TheModal from './components/TheModal.vue';
/* import TheModal from '../public/'; */
export default {
  components: {
    TheModal,
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;1,200;1,300;1,500&display=swap');
*{
  margin: 0;
  padding: 0;
  overflow: hidden;
}
#app {
  font-family: 'Poppins', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
.wrapper{
  width: 100%;
  height: 100vh;
  background: linear-gradient(to left, rgb(158, 56, 146), rgb(3, 117, 223));;
  display: flex;
  align-items: center;
  justify-content: center;
}
.wrapper::after {
  content: '';
  width: 100%;
  height: 100vh;
  position: absolute;
  top: 0;
  left: 0;
  background: url('../public/dots-100.png');
  background-size: 100%;
  background-repeat: repeat;
  background-position: center;
  opacity: 0.07;
  z-index: 1;
}
</style>
