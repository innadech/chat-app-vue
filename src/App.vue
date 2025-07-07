<script>
import HeaderChat from './components/HeaderChat.vue'
import ContentChat from './components/ContentChat.vue'
import FooterChat from './components/FooterChat.vue'
import EnterChat from './components/EnterChat.vue'
import SlideModalChat from './components/SlideModalChat.vue'

export default {
  components: {
    HeaderChat,
    ContentChat,
    FooterChat,
    EnterChat,
    SlideModalChat,
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
      <HeaderChat caption="Chat" />
      <ContentChat
        v-bind:nicknames="nicknames"
        v-on:message-updated="messages = $event"
      />
      <FooterChat v-on:message-submitted="messages.push($event)" />
      <EnterChat />
      <SlideModalChat
        caption="Your nickname:"
        v-on:login-submitted="nicknames.push($event)"
      />
    </div>
  </div>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
