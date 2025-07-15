<script>
import UiHeaderChat from './ui/UiHeaderChat.vue'
import MessageList from './components/MessageList.vue'
import MessageSubmitter from './components/MessageSubmitter.vue'
import NicknameList from './components/NicknameList.vue'
import NicknameSubmitter from './components/NicknameSubmitter.vue'

export default {
  components: {
    UiHeaderChat,
    MessageList,
    MessageSubmitter,
    NicknameList,
    NicknameSubmitter,
  },

  data() {
    return {
      nicknames: [],
      messages: [],
      message: '',
    }
  },
}
</script>

<template>
  {{ nicknames }}
  {{ messages }}
  {{ message }}
  <div class="main flex f_centered light">
    <div class="chat">
      <UiHeaderChat />

      <div class="content flex f_tile">
        <div class="left">
          <MessageList v-bind:messages="messages" />
        </div>
        <div class="right">
          <NicknameList
            v-bind:nicknames="nicknames"
            v-bind:message="message"
            v-on:update-message="message = $event"
          />
        </div>
      </div>

      <div class="footer">
        <div class="wrap-send-message flex f_tile">
          <MessageSubmitter v-on:message-submitted="messages.push($event)" />
        </div>
      </div>

      <NicknameSubmitter v-on:nickname-submitted="nicknames.push($event)" />
    </div>
  </div>
</template>

<!-- v-on:message-submitted="message = $event" -->
