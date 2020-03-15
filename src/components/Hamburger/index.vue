<template>
  <div id="hamburger-container" :class="[{dark: dark}, position]" class="hamburger-container">
    <div class="sidenav">
      <div :class="{'active':isActive}" class="sidenav-toggler d-none d-xl-block" data-action="sidenav-unpin" @click="toggleClick">
        <div class="sidenav-toggler-inner">
          <i class="sidenav-toggler-line" />
          <i class="sidenav-toggler-line" />
          <i class="sidenav-toggler-line" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Hamburger',
  props: {
    isActive: {
      type: Boolean,
      default: false
    },
    dark: {
      type: Boolean,
      default: false
    },
    position: {
      type: String,
      default: ''
    }
  },
  methods: {
    toggleClick() {
      this.$emit('toggleClick')
    }
  }
}
</script>

<style lang="scss" scoped>
.hamburger-container {
  float: left;
  cursor: pointer;
  transition: background .3s;
  -webkit-tap-highlight-color:transparent;
}
.hamburger-container.right {
  float: right;
}
.sidenav .sidenav-toggler {
  padding: 19px;
}
.sidenav-toggler-inner {
  position: relative;
}
.sidenav-toggler-inner, .sidenav-toggler-line {
  width: 18px;
  transition: all .15s ease;
}
.sidenav-toggler.active .sidenav-toggler-line:first-child, .sidenav-toggler.active .sidenav-toggler-line:last-child {
  width: 13px;
  transform: translateX(5px);
}
.sidenav-toggler-line:not(:last-child) {
  margin-bottom: 3px;
}
.sidenav-toggler-line {
  position: relative;
  display: block;
  height: 2px;
  background-color: #fff;
}
.hamburger-container.dark .sidenav-toggler-line {
  background-color: #000;
}
</style>
