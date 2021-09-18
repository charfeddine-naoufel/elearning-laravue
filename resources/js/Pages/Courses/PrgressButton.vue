<template>
  <div>
    <button
      class="
        bg-transparent
        hover:bg-blue-500
        text-blue-700
        font-semibold
        hover:text-white
        py-2
        px-4
        border border-blue-500
        hover:border-transparent
        rounded
      "
      @click="toggleWatchVideo(videoId)"
    >
      Finished ?
    </button>
  </div>
</template>

<script>
export default {
  props: ['videoId'],
  methods: {
  
    toggleWatchVideo() {
      axios
        .post("/togglewatched", { id: this.videoId })
        .then((response) => {
          console.log(response.data)
        })
        .catch((error) => {
          console.error("There was an error!", error);
        });
    },
  },
};
</script>

<style lang="scss" scoped>
</style>