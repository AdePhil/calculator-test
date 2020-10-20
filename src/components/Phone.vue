<template>
  <div class="phone">
    <div class="fcamera"></div>
    <div class="clens"></div>
    <div class="speaker"></div>
    <div class="screen">
      <slot></slot>
    </div>
    <div class="lock_btn"></div>
    <div class="volume_btn"></div>
    <div class="task_bar"></div>
  </div>
</template>

<style lang="scss" scoped>
.phone {
  background-color: #000;
  height: 550px;
  width: 280px;
  border-top-left-radius: 140px 25px;
  border-top-right-radius: 140px 25px;
  border-bottom-left-radius: 140px 25px;
  border-bottom-right-radius: 140px 25px;
  margin: 0 auto;
}

.fcamera {
  position: absolute;
  background-color: #212122;
  height: 10px;
  width: 10px;
  border-radius: 10px;
  margin-top: 25px;
  margin-left: 35px;
}

.clens {
  position: absolute;
  background-color: #0f0f0f;
  height: 5px;
  width: 5px;
  border-radius: 5px;
  margin-top: 27px;
  margin-left: 38px;
}

.speaker {
  position: absolute;
  background-color: #171717;
  height: 15px;
  width: 15px;
  border-radius: 10px;
  margin-top: 22px;
  margin-left: 130px;
}

.screen {
  background-color: #212122;
  position: absolute;
  height: 450px;
  width: 260px;
  margin-left: 10px;
  margin-top: 50px;
}

.lock_btn {
  background-color: #080808;
  position: absolute;
  height: 35px;
  width: 3px;
  margin-left: 280px;
  margin-top: 75px;
  border-top-right-radius: 3px 3px;
  border-bottom-right-radius: 3px 3px;
}

.volume_btn {
  background-color: #080808;
  position: absolute;
  height: 75px;
  width: 3px;
  margin-top: 100px;
  margin-left: -3px;
  border-top-left-radius: 3px 3px;
  border-bottom-left-radius: 3px 3px;
}
</style>
