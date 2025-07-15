<script>
export default {
  props: ['nickname', 'message'],
  emits: ['message-updated'],

  data() {
    return {
      localMessage: this.message,
    }
  },

  methods: {
    pingNickname(nickname) {
      if (this.localMessage.indexOf(nickname) !== -1) {
        return
      } else
        this.$emit('message-updated', { nickname, message: this.localMessage })
    },
  },
}
</script>

<template>
  <div v-on:click="pingNickname(nickname)">
    <span>{{ nickname }}</span>
  </div>
</template>
