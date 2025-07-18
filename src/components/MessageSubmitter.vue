<script>
export default {
  props: ['pingingNickname'],

  emits: ['message-submitted'],

  data() {
    return {
      message: '',
    }
  },

  methods: {
    handleClick() {
      if (this.message !== '') {
        const m = this.getPingingName() + this.message
        this.$emit('message-submitted', m)
        this.message = ''
      }
    },

    getPingingName() {
      if (this.pingingNickname === '') {
        return ''
      } else {
        return '@' + this.pingingNickname + ': '
      }
    },
  },
}
</script>

<template>
  <input
    v-bind:value="getPingingName() + message"
    v-on:input="message = $event.target.value.replace(getPingingName(), '')"
    type="text"
    spellcheck="false"
    id="input_msg"
  />
  <input ref="elInput" type="submit" v-on:click="handleClick" />
</template>
<!-- v-on:input="console.log($event.target.value)" -->
