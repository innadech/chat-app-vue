<script>
export default {
  // props: ['pingingNickname'],

  emits: ['message-submitted'],

  data() {
    return {
      pingingNickname: 'Inna',
      message: 'ты где ?',
    }
  },

  methods: {
    handleClick() {
      if (this.message !== '') {
        this.$emit('message-submitted', this.message)
        this.message = ''
      }
    },
  },
}
</script>

<template>
  {{ message }}
  <input
    v-bind:value="'@' + pingingNickname + ': ' + message"
    v-on:input="
      message = $event.target.value.replace('@' + pingingNickname + ': ', '')
    "
    type="text"
    spellcheck="false"
    id="input_msg"
  />
  <input ref="elInput" type="submit" v-on:click="handleClick" />
</template>
<!-- v-on:input="console.log($event.target.value)" -->
