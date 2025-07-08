<script>
import NicknameList from './components/2/NicknameList.vue'
import UiHeaderChat from './ui/UiHeaderChat.vue'

export default {
  components: { UiHeaderChat, NicknameList },
}
</script>

<template>
  <div class="main flex f_centered light">
    <div class="chat">
      <UiHeaderChat />

      <div class="content flex f_tile">
        <div class="left">
          <div class="wrap-chat-flow">
            <div class="chat-flow" spellcheck="false"></div>
          </div>
        </div>
        <div class="right">
          <NicknameList />
        </div>
      </div>

      <FooterChat v-on:message-submitted="messages.push($event)" />
      <EnterChat />
      <SlideModalChat
        caption="Your nickname:"
        v-on:login-submitted="nicknames.push($event)"
      />
    </div>
  </div>
</template>
