<template>
  <input :value="value" @input="onInput" />
</template>

<script>
export default {
  props: {
    value: String,
  },
  methods: {
    onInput(evt) {
      debugger
      this.$emit('input', evt.target.value)
    }
  }
}
</script>
