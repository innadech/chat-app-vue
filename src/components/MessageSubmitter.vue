<script>
export default {
  emits: ['message-submitted'],

  data() {
    return {
      message: '',
    }
  },

  methods: {
    handleClick() {
      if (this.message !== '') {
        this.$emit('message-submitted', this.message)
        this.message = ''
      }
    },
  },
}
</script>

<template>
  <input
    v-bind:value="message"
    v-on:input="message = $event.target.value"
    type="text"
    spellcheck="false"
    id="input_msg"
  />
  <input ref="elInput" type="submit" v-on:click="handleClick" />
</template>
