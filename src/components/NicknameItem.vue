<script>
export default {
  props: ['nickname'],

  methods: {
    sendPingNickname(event) {
      const textContent = event.target.textContent
      console.log(textContent)
      this.$emit('sendping-nickname', textContent)
    },
  },
}
</script>

<template>
  <div v-on:click="sendPingNickname">
    <span>{{ nickname }}</span>
  </div>
</template>
