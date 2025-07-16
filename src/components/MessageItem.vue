<script>
export default {
  props: ['message'],
}
</script>

<template>
  <div>
    <div class="msg-line">
      <span>{{ message }}</span>
    </div>
  </div>
</template>
