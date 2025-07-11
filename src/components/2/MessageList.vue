<script>
export default {
  props: [messages],
}
</script>

<template>
  <div class="wrap-chat-flow">
    <div class="chat-flow" spellcheck="false">
      <div class="msg-line" v-for="(message, idx) of messages" v-bind:key="idx">
        <span>{{ message }}</span>
      </div>
    </div>
  </div>
</template>
