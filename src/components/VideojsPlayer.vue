<template>
  <video ref="videojsPlayer" class="video-js"></video>
</template>

<script>
import videojs from "video.js";
import video_zhCN from "video.js/dist/lang/zh-CN.json";
import video_en from "video.js/dist/lang/en.json";

videojs.addLanguage("zh-CN", video_zhCN);
videojs.addLanguage("en", video_en);

export default {
  name: "VideojsPlayer",
  props: {
    options: {
      type: Object,
      default() {
        return {};
      }
    }
  },
  data() {
    return {
      player: null
    };
  },
  mounted() {
    let that = this;
    this.player = videojs(this.$refs.videojsPlayer, this.options, function() {
      that.$emit("playerReady", this);
    });
  },
  beforeDestroy() {
    if (this.player) {
      this.player.dispose();
      this.$emit("playerDestroyed");
    }
  }
};
</script>
