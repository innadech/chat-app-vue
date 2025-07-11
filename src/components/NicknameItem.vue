<script>
export default {
  props: ['nickname'],
  emits: ['ping-nickname'],

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
  <div>
    <span v-on:ping-nickname="pingNickname">{{ nickname }}</span>
  </div>
</template>
