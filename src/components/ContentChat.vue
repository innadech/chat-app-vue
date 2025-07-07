<script>
export default {
  props: ['nicknames', 'currentMessage'],

  emits: ['message-updated'],

  data() {
    return {
      nickname: '',
    }
  },

  methods: {
    pingNickname(nickname) {
      if (currentMessage.indexOf(`@${nickname}`) !== -1) {
        return
      } else this.$emit('message-updated', `@${nickname} ${currentMessage}`)
    },
  },
}
</script>

<template>
  <div class="content flex f_tile">
    <div class="left">
      <div class="wrap-chat-flow">
        <div class="chat-flow" spellcheck="false"></div>
      </div>
    </div>
    <div class="right">
      <div class="nickname-list">
        <div v-for="(nickname, idx) of nicknames" v-bind:key="idx">
          <span v-on:ping-nickname="pingNickname">{{ nickname }}</span>
        </div>
      </div>
    </div>
  </div>
</template>
