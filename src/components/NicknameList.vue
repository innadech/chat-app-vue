<script>
import NicknameItem from './NicknameItem.vue'

export default {
  components: { NicknameItem },

  props: ['nicknames'],
}
</script>

<template>
  <div class="nickname-list">
    <NicknameItem
      v-for="(nickname, idx) of nicknames"
      v-bind:key="idx"
      v-bind:nickname="nickname"
      v-on:click="$emit('forwardping-nickname', nickname)"
    />
  </div>
</template>
