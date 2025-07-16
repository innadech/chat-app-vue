<script>
import MessageItem from './MessageItem.vue'
export default {
  components: { MessageItem },

  props: ['messages'],
}
</script>

<template>
  <div class="wrap-chat-flow">
    <div class="chat-flow" spellcheck="false">
      <MessageItem
        v-for="(message, idx) of messages"
        v-bind:key="idx"
        v-bind:message="message"
      />
    </div>
  </div>
</template>
