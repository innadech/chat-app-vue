<script>
export default {
  props: ['messages'],
}
</script>

<template>
  <div class="wrap-chat-flow">
    <div class="chat-flow" spellcheck="false">
      <div v-for="(message, idx) of messages" v-bind:key="idx">
        <div class="msg-line">
          <span>{{ message }}</span>
        </div>
      </div>
    </div>
  </div>
</template>
