<script>
import NicknameItem from './NicknameItem.vue'

export default {
  components: { NicknameItem },

  props: ['nicknames'],

  methods: {
    forwardPingNickname(text) {
      console.log(text)
      this.$emit('forwardping-nickname', text)
    },
  },
}
</script>

<template>
  <div class="nickname-list">
    <NicknameItem
      v-for="(nickname, idx) of nicknames"
      v-bind:key="idx"
      v-bind:nickname="nickname"
      v-on:sendping-nickname="forwardPingNickname"
    />
  </div>
</template>
