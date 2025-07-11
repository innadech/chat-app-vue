<script>
import NicknameList from './components/2/NicknameList.vue'
import MessageList from './components/2/MessageList.vue'
import UiHeaderChat from './ui/UiHeaderChat.vue'
import MessageSubmitter from './components/2/MessageSubmitter.vue'
import LoginSubmitter from './components/2/LoginSubmitter.vue'

export default {
  components: {
    UiHeaderChat,
    NicknameList,
    MessageList,
    MessageSubmitter,
    LoginSubmitter,
  },

  data() {
    return {
      nicknames: [],
      messages: [],
    }
  },
}
</script>

<template>
  <div class="main flex f_centered light">
    <div class="chat">
      <UiHeaderChat />

      <div class="content flex f_tile">
        <div class="left">
          <MessageList v-bind:messages="messages" />
        </div>
        <div class="right">
          <NicknameList />
        </div>
      </div>

      <div class="footer">
        <div class="wrap-send-message flex f_tile">
          <MessageSubmitter v-on:message-submitted="messages.push($event)" />
        </div>
      </div>

      <LoginSubmitter
        caption="Your nickname:"
        v-on:login-submitted="nicknames.push($event)"
      />
    </div>
  </div>
</template>
