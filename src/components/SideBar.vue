<template>

    <!-- Off-canvas -->
    <div class="gs-off-canvas" id="off-canvas" v-on:click="closeSidebar()">
      <div class="gs-off-canvas__bar" id="off-canvas-bar" v-on:click="preventClosingSidebar()">
        <p class="gs-off-canvas__label" id="label-city"> Город </p>
        <hr>
        <button class="gs-off-canvas__btn gs-nav-btn active" id="gsv-btn" v-on:click="switchCity('gsv')"> <i class="gs-icon-ok"> </i> Гусев</button>
        <button class="gs-off-canvas__btn gs-nav-btn" id="kgd-btn" v-on:click="switchCity('kgd')"> <i class="gs-icon-ok"> </i> Калининград</button>
      </div>
    </div>

</template>

<script>
export default {
  name: 'sidebar',
  data: function () {
    return {
      preventClosing: false
    }
  },
  methods: {
    switchCity: function (city) {
      this.$emit('switchCity', city)
    },
    showGusevItems: function () {
      this.$emit('showGusevItems')
    },
    showKaliningradItems: function () {
      this.$emit('showKaliningradItems')
    },
    closeSidebar: function () {
      if (!this.preventClosing) {
        this.$emit('closeSidebar')
      }

      this.preventClosing = false
    },
    preventClosingSidebar: function () {
      this.preventClosing = true
    }
  }
}
</script>

<style lang="scss">

@import '../assets/scss/sidebar.scss';

</style>