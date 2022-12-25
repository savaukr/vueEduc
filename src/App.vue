<template>
  <div>
    <div>Counts of likes: {{ likes }}</div>
    <button @click="likes = likes + 1">Increase like</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      likes: 0,
    };
  },
};
</script>
<style></style>
