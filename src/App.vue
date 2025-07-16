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
      pingName: '',
      currentMessage: '',
    }
  },

  methods: {
    addListNickname() {
      if (!this.nicknames.includes(this.currentNickname)) {
        this.nicknames.push(this.currentNickname)
        return true
      } else {
        return false
      }
    },

    login(e) {
      this.currentMessage = ''
      this.currentNickname = e
      let isOk = this.addListNickname()
      if (isOk) {
        this.systemMessage()
      }
    },
    systemMessage() {
      const currentMessageSystem =
        this.currentNickname + ': ' + 'вошел(ла) в чат' + this.currentMessage
      this.messages.push(currentMessageSystem)
    },
    sendMessage(e) {
      console.log(e)
      this.currentMessage = this.currentNickname + ': ' + e
      this.messages.push(this.currentMessage)
    },
    addPingNicknameToMessage(e) {
      this.pingName = e
      if (this.currentMessage.indexOf(this.pingName) !== -1) {
        return
      } else {
        this.currentMessage = '@' + this.pingName + this.currentMessage
      }
    },

    // addPingNicknameToMessage(e) {
    //   this.pingName = e
    //   if (this.currentMessage.indexOf('@') !== -1) {
    //     const spaceIndex = this.currentMessage.indexOf(' ')
    //     if (spaceIndex !== -1) {
    //       this.currentMessage = this.currentMessage.substring(spaceIndex + 1)
    //     } else {
    //       this.currentMessage = ''
    //     }
    //   }
    //   if (this.pingName) {
    //     this.currentMessage = '@' + this.pingName + this.currentMessage
    //   }
    // },
  },
}
</script>

<template>
  {{ currentMessage }}
  {{ pingName }}

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
            v-on:forwardping-nickname="addPingNicknameToMessage"
          />
        </div>
      </div>

      <div class="footer">
        <div class="wrap-send-message flex f_tile">
          <MessageSubmitter v-on:message-submitted="sendMessage" />
        </div>
      </div>

      <NicknameSubmitter v-on:nickname-submitted="login" />
      <!-- <NicknameSubmitter v-on:nickname-submitted="login($event)" /> -->
    </div>
  </div>
</template>

<!-- elButton.onclick = onClickButton -->

<!-- v-on:message-submitted="message = $event" -->
