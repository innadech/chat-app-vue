<script>
import NicknameItem from './NicknameItem.vue'

export default {
  props: [nicknames],
  components: { NicknameItem },
}
</script>

<template>
  <div class="nickname-list">
    <NicknameItem
      v-for="(nickname, idx) of nicknames"
      v-bind:key="idx"
      v-bind:nickname="nickname"
    />
  </div>
</template>
