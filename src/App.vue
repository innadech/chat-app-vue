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
      currentNickname: '',
      pingingNickname: '',
    }
  },

  methods: {
    isNewUser() {
      return !this.nicknames.includes(this.currentNickname)
    },

    login(e) {
      this.currentNickname = e
      if (this.isNewUser()) {
        this.systemMessage()
        this.nicknames.push(this.currentNickname)
      }
    },

    systemMessage() {
      const sysMsg = '{system} ' + this.currentNickname + ' вошел(ла) в чат'
      this.messages.push(sysMsg)
    },

    sendMessage(e) {
      this.messages.push(e)
      this.pingingNickname = ''
    },
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
          <NicknameList
            v-bind:nicknames="nicknames"
            v-on:forwardping-nickname="pingingNickname = $event"
          />
        </div>
      </div>

      <div class="footer">
        <div class="wrap-send-message flex f_tile">
          <MessageSubmitter
            v-on:message-submitted="sendMessage"
            v-bind:pinging-nickname="pingingNickname"
          />
        </div>
      </div>

      <NicknameSubmitter v-on:nickname-submitted="login" />
      <!-- <NicknameSubmitter v-on:nickname-submitted="login($event)" /> -->
    </div>
  </div>
</template>

<!-- elButton.onclick = onClickButton -->

<!-- v-on:message-submitted="message = $event" -->
