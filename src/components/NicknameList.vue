<script>
import NicknameItem from './NicknameItem.vue'

export default {
  components: { NicknameItem },

  props: ['nicknames', 'message'],
  emits: ['update-message'],

  data() {
    return {
      localMessage: this.message,
    }
  },
  methods: {
    updateMessage(newMessage) {
      this.localMessage = newMessage
      this.$emit('update-message', newMessage)
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
      v-bind:message="localMessage"
      v-on:message-updated="updateMessage($event)"
    />
  </div>
</template>
