<template>
  <div id="app" :class="deviceClass">
    <transition name="page">
      <router-view class="page"></router-view>
    </transition>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      deviceClass: ''
    }
  },
  created () {
    // 判断设备类型
    if (/iPad|iPhone|iPod/.test(navigator.userAgent)) {
      this.deviceClass = 'ios-device'
    } else {
      this.deviceClass = 'android-device'
    }
  }
}
</script>

<style scoped>
  .page-enter-active,
  .page-leave-active,
  .ios-device .page-enter-active,
  .ios-device .page-leave-active
  {
    -webkit-transition-duration: 500ms;
    transition-duration: 500ms;
    -webkit-transition-timing-function: cubic-bezier(.36, .66, .04, 1);
    transition-timing-function: cubic-bezier(.36, .66, .04, 1);
    -webkit-transition-property: opacity, -webkit-transform;
    transition-property: opacity, transform;
  }

  .android-device .page-enter-active,
  .android-device .page-leave-active
  {
    -webkit-transition-duration: 200ms;
    transition-duration: 200ms;
    -webkit-transition-timing-function: cubic-bezier(0.4, 0.6, 0.2, 1);
    transition-timing-function: cubic-bezier(0.4, 0.6, 0.2, 1);
  }

  [transition-direction="forward"] .page-enter {
    -webkit-transform: translate3d(100%, 0, 0);
    transform: translate3d(100%, 0, 0);
    opacity: 1;
    z-index: 2;
  }
  [transition-direction="forward"] .page-enter-active {
    box-shadow: 0 0 10px rgba(0,0,0,.15);
  }
  [transition-direction="forward"] .page-enter-to {
    -webkit-transform: translate3d(0, 0, 0);
    transform: translate3d(0, 0, 0);
    opacity: 1;
    z-index: 2;
  }
  [transition-direction="forward"] .page-leave {
    -webkit-transform: translate3d(0, 0, 0);
    transform: translate3d(0, 0, 0);
    opacity: 0.8;
    z-index: 1;
  }
  [transition-direction="forward"] .page-leave-to {
    -webkit-transform: translate3d(-33%, 0, 0);
    transform: translate3d(-33%, 0, 0);
    opacity: 0;
    z-index: 1;
  }

  [transition-direction="back"] .page-enter {
    -webkit-transform: translate3d(-33%, 0, 0);
    transform: translate3d(-33%, 0, 0);
    opacity: 0.8;
    z-index: 1;
  }
  [transition-direction="back"] .page-enter-to {
    -webkit-transform: translate3d(0, 0, 0);
    transform: translate3d(0, 0, 0);
    opacity: 1;
    z-index: 1;
  }
  [transition-direction="back"] .page-leave {
    -webkit-transform: translate3d(0, 0, 0);
    transform: translate3d(0, 0, 0);
    opacity: 1;
    z-index: 2;
  }
  [transition-direction="back"] .page-leave-active {
    box-shadow: 0 0 10px rgba(0,0,0,.15);
  }
  [transition-direction="back"] .page-leave-to {
    -webkit-transform: translate3d(100%, 0, 0);
    transform: translate3d(100%, 0, 0);
    opacity: 1;
    z-index: 2;
  }

</style>
