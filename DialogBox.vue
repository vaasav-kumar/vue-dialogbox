<template>
  <div class="blur-bg" v-if="showPopup">
    <div class="popup-box">
      <div class="heading">
        <h5 class="title">{{title}}</h5>
        <span class="close-button" @click="closePopup">&times;</span>
      </div>

      <div class="body">
        <slot name="body" />
      </div>

      <div class="footer">
        <slot name="footer" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DialogBox',
  props: {
    title: String,
    showPopup: Boolean,
    closePopup: Function,
    header: {
      type: Boolean,
      default: true
    },
    footer: {
      type: Boolean,
      default: true
    }
  }
}
</script>

<style scoped>
.blur-bg {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  background: rgba(0,0,0,0.6);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}
.popup-box {
  background: #ffffff;
  border-radius: 25px;
  width: 60%;
  padding: 10px;
}
.close-button {
  color: #000000;
  font-size: 24px;
  font-weight: 500;
  cursor: pointer;
}
.title {
  font-size: 20px;
  font-weight: 400;
  color: #000000;
}
.heading {
  padding: 20px;
  display: flex;
  width: 100%;
  justify-content: space-between;
  border-bottom: 1px solid #e4e7e7;
}

.footer {
  display: flex;
  justify-content: space-evenly;
  padding: 20px;
  border-top: 1px solid #e4e7e7;
}
.body {
  padding: 20px;
}

@media screen and (max-width: 519px) {
  .popup-box {
    width: 90%;
  }
}
</style>
