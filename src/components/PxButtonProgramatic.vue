<template>
  <button
  v-on:click="buttonClick"
  class="bg-transparent hover:bg-green-500 text-green-700 font-semibold hover:text-white py-2 px-2 border border-green-500 hover:border-transparent rounded">
  <beat-loader
      v-show="isLoading"
      :loading="isLoading"
      color="#68d391"
      :size="8"
    />
  <slot v-if="!isLoading"></slot>
  </button>
</template>

<script>
export default {
  name: 'PxButtonProgramatic',
  props: {
    isLoading: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    buttonClick() {
      this.$emit('click')
    }
  }
}
</script>
