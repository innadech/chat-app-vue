<script>
import NicknameItem from './NicknameItem.vue'

export default {
  components: { NicknameItem },
}
</script>

<template>
  <div class="nickname-list">
    <NicknameItem v-for="(nickname, idx) of nicknames" v-bind:key="idx" />
  </div>
</template>
