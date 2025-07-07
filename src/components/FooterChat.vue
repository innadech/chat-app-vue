<script>
export default {
  // props: ['caption'],

  emits: ['message-submitted', 'edited-fruit'],

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
  <div class="footer">
    <div class="wrap-send-message flex f_tile">
      <input type="text" spellcheck="false" id="input_msg" />
      <input
        ref="elInput"
        type="submit"
        v-bind:value="message"
        v-on:click="handleClickButton"
      />
    </div>
  </div>
</template>

<input
  v-bind:value="fruit"
  v-on:input="$emit('edited-fruit', $event.target.value)"
/>
