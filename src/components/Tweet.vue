<template>
  <div class="tweet" v-if="tweet && tweet.user">
    <ProfileImage :image="tweet.user.image" />

    <div class="body">
      <div class="top">
        <User :userData="tweet.user" />
        <Timestamp :time="tweet.timestamp" />
      </div>

      <Message :message="tweet.message" />
      <Actions />
    </div>

    <i class="fas fa-ellipsis-h"></i>
  </div>
  <div v-else class="loading-tweet">
    Loading tweet... (Debug: {{ tweet ? 'Tweet object exists but might be missing user property' : 'No tweet object' }})
  </div>
</template>

<script setup>
import { onMounted, watch } from 'vue';
import ProfileImage from './ProfileImage.vue';
import User from './User.vue';
import Timestamp from './Timestamp.vue';
import Message from './Message.vue';
import Actions from './Actions.vue';

const props = defineProps({
  tweet: {
    type: Object,
    required: true
  }
});

// Add debugging to see if the tweet prop is being received correctly
onMounted(() => {
  console.log('Tweet component mounted, tweet prop:', props.tweet);
  if (props.tweet) {
    console.log('Tweet user:', props.tweet.user);
  }
});

// Watch for changes to the tweet prop
watch(() => props.tweet, (newTweet) => {
  console.log('Tweet prop changed:', newTweet);
}, { immediate: true });
</script>

<style scoped>
a {
  color: #42b983;
}
</style>
