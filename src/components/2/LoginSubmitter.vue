<script>
export default {
  props: ['caption'],
  emits: ['login-submitted'],

  data() {
    return {
      nickname: '',
    }
  },

  methods: {
    handleClickLoginButton() {
      if (this.nickname !== '') {
        this.$emit('login-submitted', this.nickname)
        this.nickname = ''
      }
    },
  },
}
</script>

<template>
  <input ref="elInput" type="checkbox" id="chk_sm" />
  <div class="slide-modal flex f_centered">
    <div class="wrap-enter-form">
      <label for="input_nickname">{{ caption }}</label>
      <input
        v-bind:value="nickname"
        type="text"
        id="input_nickname"
        spellcheck="false"
        autocomplite="off"
        required
      />
      <div class="wrap-enter-button">
        <label v-on:click="handleClickLoginButton" for="chk_sm" id="btn_enter"
          >Enter the chat</label
        >
      </div>
    </div>
  </div>
</template>
