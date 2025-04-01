<template>
  <span class="timestamp">{{ time }}</span>
</template>

<script setup>
defineProps({
  time: {
    type: String,
    required: true
  }
});
</script>
