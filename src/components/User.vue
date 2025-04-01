<template>
  <span class="user">
    <span class="name">{{ userData.name }}</span>
    <span class="handle">@{{ userData.handle }}</span>
  </span>
</template>

<script setup>
defineProps({
  userData: {
    type: Object,
    required: true
  }
});
</script>
