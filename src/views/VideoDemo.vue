<template>
  <div>
    <VideojsPlayer :options="videoOptions" @playReady="handlePlayerReady"/>
  </div>
</template>

<script>
import VideojsPlayer from "../components/VideojsPlayer.vue";
import "videojs-flash";
import "video.js/dist/video-js.css";

export default {
  name: "VideoDemo",
  components: {
    VideojsPlayer
  },
  data() {
    return {
      videoOptions: {
        // width: "800px",
        // height: "600px",
        autoplay: true,
        controls: true,
        techOrder: ["flash", "html5"],
        preload: "auto",
        liveui: true,
        language: "zh-CN",
        muted: true,
        fluid: true,
        controlBar: {
          volumePanel: {
            inline: false
          }
        },
        // children: [
        //   { name: "playToggle" }, // 播放按钮
        //   { name: "currentTimeDisplay" }, // 当前已播放时间
        //   { name: "progressControl" }, // 播放进度条
        //   { name: "durationDisplay" }, // 总时间
        //   {
        //     // 倍数播放
        //     name: "playbackRateMenuButton",
        //     playbackRates: [0.5, 1, 1.5, 2, 2.5]
        //   },
        //   {
        //     name: "volumePanel", // 音量控制
        //     inline: false // 不使用水平方式
        //   },
        //   { name: "FullscreenToggle" } // 全屏
        // ],
        sources: [
          {
            // src: "rtmp://222.143.52.111:19975/live/000041010035_1_1",
            src: "rtmp://222.143.52.111:19975/live/000041010016_1_1",
            type: "rtmp"
          }
        ]
      }
    };
  },
  methods: {
    handlePlayerReady(playRef) {}
  }
};
</script>
