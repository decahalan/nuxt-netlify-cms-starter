<template>
  <div class="notification">
    <div class="notification---icon">
      <i class="fa" :class="iconClass" />
    </div>
    <div>
      <p v-text="status.text"></p>
    </div>
    <button
      type="button"
      class="notification--remove"
      @click="removeNotification()"
    >
      <i class="fa fa-times" />
    </button>
  </div>
</template>

<script>
export default {
  name: 'form-notification',
  props: {
    status: {
      type: Object
    }
  },
  computed: {
    iconClass() {
      if (this.status.code) {
        return 'fa-check'
      } else {
        return 'fa-exclamation'
      }
    }
  },
  mounted() {
    // this.countdown = setTimeout(this.removeNotification, 3000)
  },
  methods: {
    removeNotification() {
      clearTimeout(this.countdown)
      this.$emit('remove-notification')
    }
  }
}
</script>

<style scoped lang="scss">
.notification {
  position: fixed;
  z-index: 5;
  box-sizing: border-box;
  top: 10px;
  right: 10px;
  width: 179px;
  padding: 20px;
  box-shadow: 0 5px 15px 0 rgba(0, 0, 0, 0.3);
  overflow: hidden;
  border-radius: 3px;
  background: white;
  color: #64b587;
  border-bottom: 5px solid #64b587;
  &--remove {
    position: absolute;
    top: 0;
    right: 0;
    font-size: 15px;
    &:hover {
      cursor: pointer;
    }
  }
}
.fa {
  position: relative;
  width: 100%;
  text-align: center;
}
.fa-check {
  color: #64b587;
}
.fa-exclamation {
  color: #e74e50;
}
button {
  border: none;
}
</style>
