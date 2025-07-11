<script>
export default {
  emits: ['nickname-submitted'],

  data() {
    return {
      nickname: '',
    }
  },

  methods: {
    handleClick() {
      if (this.nickname !== '') {
        this.$emit('nickname-submitted', this.nickname)
        this.nickname = ''
      }
    },
  },
}
</script>

<template>
  {{ nickname }}
  <input type="checkbox" id="chk_sm" />
  <div class="slide-modal flex f_centered">
    <div class="wrap-enter-form">
      <label for="input_nickname">Your nickname:</label>
      <input
        v-bind:value="nickname"
        v-on:input="nickname = $event.target.value"
        type="text"
        id="input_nickname"
        spellcheck="false"
        autocomplite="off"
        required
      />
      <div v-on:click="handleClick" class="wrap-enter-button">
        <label v-on:click="handleClick" for="chk_sm" id="btn_enter">
          Enter the chat
        </label>
      </div>
    </div>
  </div>
</template>
