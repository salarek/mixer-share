<template>
  <v-row justify="center" align="center">
    <v-content>
      <youtube
        :video-id="getId(videoId)"
        ref="youtube"
        @playing="playing"
      ></youtube>
      <v-text-field
        label="Main input"
        :rules="rules"
        hide-details="auto"
      ></v-text-field>
    </v-content>
  </v-row>
</template>

<script>
import { getIdFromUrl } from "vue-youtube";
export default {
  name: "IndexPage",
  data() {
    return {
      videoId: "https://www.youtube.com/watch?v=0zxqXMSG4xI&list=LL&index=1",
    };
  },
  methods: {
    getId(url) {
      return getIdFromUrl(url);
    },
    playing() {
      console.log("\o/ we are watching!!!");
    },
    async playVideo() {
      await this.player.playVideo();
      // Do something after the playVideo command
    },
  },
  computed: {
    player() {
      return this.$refs.youtube.player;
    },
  },
};
</script>
