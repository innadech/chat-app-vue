<script>
export default {
  // props: ['caption'],

  emits: ['message-submitted'],

  data() {
    return {
      message: '',
    }
  },

  methods: {
    handleClickButton() {
      if (this.message !== '') {
        this.$refs.elInput('message-submitted', this.message)
        this.fruit = ''
      }
    },
  },
}
</script>

<template>
  <input v-bind:value="message" type="text" spellcheck="false" id="input_msg" />
  <input ref="elInput" type="submit" v-on:click="handleClickButton" />
</template>
