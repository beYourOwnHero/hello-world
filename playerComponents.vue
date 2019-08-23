<style lang="less" scoped>
.offButton {
  position: absolute;
  width: 50px;
  height: 24px;
  top: -24px;
  right: 27px;
  border-top: 4px solid rgba(108, 108, 108, 0.6);
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
  background: #383838;
}
#playerComponents {
  .dn {
    display: none;
  }

  .audioBody {
    width: 100%;
    height: 60px;
    border-top: 4px solid rgba(108, 108, 108, 0.6);
    background: url("../../../assets/details_images/orthogon.png") 100%;

    .audioOut {
      display: flex;
      flex-wrap: nowrap;
      justify-content: center;
      width: 100%;
      height: 60px;

      .icon {
        cursor: pointer;
        margin: 8px 0px 0px 0px;
        width: 36px;
        height: 36px;
        color: #cccccc;
      }

      .icon02 {
        cursor: pointer;
        margin: 16px 16px 0px 16px;
        width: 20px;
        height: 20px;
        color: #a2a2a2;
      }

      .icon03 {
        cursor: pointer;
        margin: 16px 16px 0px 16px;
        width: 20px;
        height: 20px;
        color: #a2a2a2;
      }

      .icon04 {
        cursor: pointer;
        margin: 21px 10px 0px 10px;
        width: 25px;
        height: 25px;
        color: #cccccc;
      }

      .extent {
        position: relative;
        width: 40%;
        height: 20px;
        margin: 16px 10px 0px 10px;

        .audioTitle {
          position: absolute;
          top: -10px;
          left: -5px;
          width: 400px;
          font-size: 14px;
          text-align: left;
          color: #ffffff;
        }
      }

      .musicTime {
        min-width: 110px;
        height: 30px;
        margin: 25px 10px 0px 10px;
        color: #ffffff;
        font-size: 14px;
      }

      // 音量样式
      .volumeSize {
        margin: 13px 10px 0px 10px;
        width: 100px;
        height: 30px;
      }
    }
  }
}
/deep/.ivu-slider .ivu-slider-wrap .ivu-slider-button-wrap {
  top: -5px;
}

/deep/.ivu-slider
  .ivu-slider-wrap
  .ivu-slider-button-wrap
  .ivu-tooltip
  .ivu-tooltip-rel {
  margin-bottom: 0px;
}

/deep/.ivu-slider
  .ivu-slider-wrap
  .ivu-slider-button-wrap
  .ivu-tooltip
  .ivu-tooltip-rel
  .ivu-slider-button {
  border: 2px solid #ffffff;
  background-color: #434343;
  width: 15px;
  height: 15px;
}

/deep/.ivu-slider .ivu-slider-wrap {
  background-color: #232323;
  height: 8px;
  border-bottom: 1.5px solid #888888;

  .ivu-slider-bar {
    height: 8px;
    background-color: #aaaaaa;
  }
}
</style>

<template>
  <div id="playerComponents">
    <audio
      ref="audio"
      class="dn"
      :src="Curl"
      :preload="audio.preload"
      @play="onPlay"
      @error="onError"
      @pause="onPause"
      @waiting="onWaiting"
      @loadedmetadata="onLoadedmetadata"
      @timeupdate="onTimeupdate"
    ></audio>
    <div class="audioBody">
      <div class="audioOut">
        <div class="offButton" title="关闭"></div>
        <!-- 上一曲 -->
        <div>
          <svg
            t="1565145408661"
            class="icon02"
            viewBox="0 0 1024 1024"
            version="1.1"
            xmlns="http://www.w3.org/2000/svg"
            p-id="1416"
            width="32"
            height="32"
          >
            <path
              d="M998.4 512V227.584c0-52.138667-56.405333-84.650667-101.546667-58.624L650.496 311.125333 404.224 453.376c-45.141333 26.026667-45.141333 91.221333 0 117.248l246.357333 142.250667 246.357334 142.250666c45.141333 26.026667 101.546667-6.485333 101.546666-58.624V512zM121.770667 865.28c57.6 0 104.704-47.104 104.704-104.704V263.424c0-57.6-47.104-104.704-104.704-104.704S17.066667 205.824 17.066667 263.424v497.237333c0 57.514667 47.104 104.618667 104.704 104.618667z"
              fill="#a2a2a2"
              p-id="1417"
            />
          </svg>
        </div>
        <!-- 播放 -->
        <div v-show="playBool" @click="startPlayOrPause" title="播放按钮">
          <svg
            t="1565084729487"
            class="icon"
            viewBox="0 0 1024 1024"
            version="1.1"
            xmlns="http://www.w3.org/2000/svg"
            p-id="2742"
            width="32"
            height="32"
          >
            <path
              d="M332.8 512V326.485333c0-33.962667 36.778667-55.210667 66.218667-38.229333l160.682666 92.757333 160.682667 92.757334c29.44 16.981333 29.44 59.477333 0 76.458666L559.701333 642.986667 399.018667 735.744c-29.44 16.981333-66.218667-4.266667-66.218667-38.229333V512z"
              fill="#ffffff"
              p-id="2743"
            />
            <path
              d="M512 66.56c245.589333 0 445.354667 199.765333 445.354667 445.354667s-199.765333 445.44-445.354667 445.44S66.56 757.589333 66.56 512 266.410667 66.56 512 66.56M512 0C229.205333 0 0 229.205333 0 512s229.205333 512 512 512 512-229.205333 512-512S794.794667 0 512 0z"
              fill="#ffffff"
              p-id="2744"
            />
          </svg>
        </div>
        <!-- 暂停 -->
        <div v-show="playBool02" @click="startPlayOrPause" title="暂停按钮">
          <svg
            t="1565086660670"
            class="icon"
            viewBox="0 0 1024 1024"
            version="1.1"
            xmlns="http://www.w3.org/2000/svg"
            p-id="3783"
            width="32"
            height="32"
          >
            <path
              d="M512 66.56c245.589333 0 445.354667 199.765333 445.354667 445.354667s-199.765333 445.44-445.354667 445.44S66.56 757.589333 66.56 512 266.410667 66.56 512 66.56M512 0C229.205333 0 0 229.205333 0 512s229.205333 512 512 512 512-229.205333 512-512S794.794667 0 512 0z"
              fill="#ffffff"
              p-id="3784"
            />
            <path
              d="M375.466667 742.4c-37.546667 0-68.266667-30.72-68.266667-68.266667V349.866667c0-37.546667 30.72-68.266667 68.266667-68.266667s68.266667 30.72 68.266666 68.266667v324.266666c0 37.546667-30.72 68.266667-68.266666 68.266667zM648.533333 742.4c-37.546667 0-68.266667-30.72-68.266666-68.266667V349.866667c0-37.546667 30.72-68.266667 68.266666-68.266667s68.266667 30.72 68.266667 68.266667v324.266666c0 37.546667-30.72 68.266667-68.266667 68.266667z"
              fill="#ffffff"
              p-id="3785"
            />
          </svg>
        </div>
        <!-- 下一曲 -->
        <div>
          <svg
            t="1565145851613"
            class="icon03"
            viewBox="0 0 1024 1024"
            version="1.1"
            xmlns="http://www.w3.org/2000/svg"
            p-id="2642"
            width="16"
            height="16"
          >
            <path
              d="M17.066667 512V227.584c0-52.138667 56.405333-84.650667 101.546666-58.624l246.357334 142.250667 246.357333 142.250666c45.141333 26.026667 45.141333 91.221333 0 117.248L364.970667 712.874667 118.613333 855.04C73.472 881.152 17.066667 848.554667 17.066667 796.416V512zM893.696 865.28c-57.6 0-104.704-47.104-104.704-104.704V263.424c0-57.6 47.104-104.704 104.704-104.704S998.4 205.824 998.4 263.424v497.237333c0 57.514667-47.104 104.618667-104.704 104.618667z"
              fill="#a2a2a2"
              p-id="2643"
            />
          </svg>
        </div>
        <!-- 进度条 -->
        <div class="extent">
          <div
            class="audioTitle"
            :title="musicName"
          >{{musicName.length > 20 ? musicName.substr(0,20) + "..." : musicName}}</div>
          <Slider v-model="sliderTime" @on-change="changeCurrentTime" show-tip="never"></Slider>
        </div>
        <!-- 音乐时间 -->
        <div class="musicTime">
          <span>{{audio.currentTime | formatSecond}}</span>
          <span>/</span>
          <span style="color: #ccc;">{{mp3MaxTime | formatSecond}}</span>
        </div>
        <!-- 音量按钮 -->
        <div @click="startMutedOrNot">
          <!-- 音量 -->
          <div v-show="!audio.muted" title="播放">
            <svg
              t="1565159197649"
              class="icon04"
              viewBox="0 0 1024 1024"
              version="1.1"
              xmlns="http://www.w3.org/2000/svg"
              p-id="3420"
              width="25"
              height="25"
            >
              <path
                d="M746.752 690.517333a33.322667 33.322667 0 0 1-16.725333-62.122666c42.410667-24.490667 68.693333-70.144 68.693333-119.04 0-46.336-23.125333-89.258667-61.952-114.858667a33.194667 33.194667 0 0 1-9.472-46.08 33.194667 33.194667 0 0 1 46.08-9.472 203.639467 203.639467 0 0 1 91.904 170.410667c0 72.533333-39.082667 140.202667-101.888 176.64-5.290667 3.072-11.008 4.522667-16.64 4.522666z"
                fill="#d8d8d8"
                p-id="3421"
              />
              <path
                d="M871.765333 768.256c-9.557333 0-19.114667-4.096-25.685333-12.032a33.288533 33.288533 0 0 1 4.437333-46.848c59.221333-49.066667 93.269333-121.173333 93.269334-197.973333 0-76.117333-33.450667-147.797333-91.818667-196.778667a33.28 33.28 0 0 1-4.096-46.848c11.776-14.08 32.853333-15.957333 46.848-4.096a322.7904 322.7904 0 0 1 115.541333 247.808c0 96.682667-42.752 187.562667-117.333333 249.258667a33.28 33.28 0 0 1-21.162667 7.509333zM669.866667 228.864c0-52.394667-60.416-81.664-101.546667-49.237333L408.064 305.834667l-30.72 24.234666H130.304c-45.994667 0-83.370667 37.290667-83.370667 83.370667v200.277333c0 45.994667 37.290667 83.370667 83.370667 83.370667h250.88l26.965333 21.248L568.32 844.373333c41.130667 32.426667 101.546667 3.072 101.546667-49.237333 0 0-25.6-149.333333-25.6-283.136s25.6-283.136 25.6-283.136z"
                fill="#d8d8d8"
                p-id="3422"
              />
            </svg>
          </div>
          <!-- 静音 -->
          <div v-show="audio.muted" title="静音">
            <svg
              t="1565173729830"
              class="icon04"
              viewBox="0 0 1024 1024"
              version="1.1"
              xmlns="http://www.w3.org/2000/svg"
              p-id="1524"
              width="25"
              height="25"
            >
              <path
                d="M633.6 512c0 141.909333 27.136 300.288 27.136 300.288 0 55.552-64.085333 86.613333-107.690667 52.309333L383.061333 730.709333l-28.586666-22.528H88.405333C39.594667 708.181333 0 668.586667 0 619.776V407.381333c0-48.810667 39.594667-88.405333 88.405333-88.405333h262.058667l32.597333-25.685333L552.96 159.402667c43.605333-34.389333 107.690667-3.328 107.690667 52.309333 0.085333 0-27.050667 158.378667-27.050667 300.288z m277.418667 0l102.4-102.4a36.309333 36.309333 0 0 0 0-51.2 36.309333 36.309333 0 0 0-51.2 0l-102.4 102.4-102.4-102.4a36.309333 36.309333 0 0 0-51.2 0 36.309333 36.309333 0 0 0 0 51.2l102.4 102.4-102.4 102.4a36.309333 36.309333 0 0 0 0 51.2 36.309333 36.309333 0 0 0 51.2 0l102.4-102.4 102.4 102.4a36.309333 36.309333 0 0 0 51.2 0 36.309333 36.309333 0 0 0 0-51.2l-102.4-102.4z"
                fill="#cccccc"
                p-id="1525"
              />
            </svg>
          </div>
        </div>

        <div class="volumeSize">
          <Slider v-model="volume" :tip-format="format" @on-change="changeVolume"></Slider>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// 时间处理函数
function realFormatSecond(second) {
  var secondType = typeof second;

  if (secondType === "number" || secondType === "string") {
    second = parseInt(second);

    var hours = Math.floor(second / 3600);
    second = second - hours * 3600;
    var mimute = Math.floor(second / 60);
    second = second - mimute * 60;

    return (
      hours + ":" + ("0" + mimute).slice(-2) + ":" + ("0" + second).slice(-2)
    );
  } else {
    return "0:00:00";
  }
}

export default {
  name: "playerComponents",
  props: ["theUrl", "ids"],
  data() {
    return {
      // details 按钮联动标识参数 (父传子)
      demo: this.ids,
      // details 按钮联动标识参数 (子传父)
      saidTheSpirit: 0,
      Curl: this.theUrl.Purl,
      Cname: this.theUrl.Pname,
      audio: {
        currentTime: 0,
        maxTime: 0,
        playing: false,
        muted: false,
        speed: 1,
        waiting: true,
        preload: "auto"
      },
      mp3MaxTime: this.theUrl.mp3time,
      playBool: true,
      playBool02: false,
      // 音乐名称
      musicName: this.theUrl.Pname,
      // 进度条
      sliderTime: 0,
      // 音量控制
      volume: 100,
      // 静音
      volumeBool: true,
      // 播放
      volumeBool02: false
    };
  },
  mounted() {
    // console.log(this.demo);
  },
  watch: {
    theUrl: {
      handler(val) {
        // console.log(val);
        this.Curl = val.Purl;
        this.musicName = val.Pname;
        this.mp3MaxTime = Number(val.mp3time);
      }
    },
    ids: {
      handler(x) {
        // console.log(x);
        // 用于控制 details 页面按钮样式变化联动
        this.ids = x;
        if (this.ids.alayerFalse == 1) {
          // 播放
          this.startPlay();
        } else if (this.ids.alayerFalse == 2) {
          // 暂停
          this.pausePlay();
        } else {
          return;
        }
      }
    },
    deep: true
  },
  methods: {
    onError(error) {
      // console.log(error);
    },
    // 播放暂停判定函数
    startPlayOrPause() {
      return this.audio.playing ? this.pausePlay() : this.startPlay();
    },
    // 开始播放
    startPlay() {
      // 子父组件传参
      this.saidTheSpirit = 1;
      this.$emit("func", this.saidTheSpirit);
      this.$refs.audio.play();
      this.playBool = false;
      this.playBool02 = true;
    },
    // 暂停
    pausePlay() {
      // 子父组件传参
      this.saidTheSpirit = 2;
      this.$emit("func", this.saidTheSpirit);
      this.$refs.audio.pause();
      this.playBool = true;
      this.playBool02 = false;
    },
    // 当音频暂停
    onPause() {
      this.audio.playing = false;
    },
    // 当录音开始播放
    onPlay(res) {
      // console.log(res);
      this.audio.playing = true;
    },
    // 当timeupdate事件大概每秒一次，用来更新音频流的当前播放时间
    onTimeupdate(res) {
      this.audio.currentTime = res.target.currentTime;
      this.sliderTime = parseInt(
        (this.audio.currentTime / this.mp3MaxTime) * 100
      );
      if (this.sliderTime === 100) {
        // 按钮切换
        this.playBool = true;
        this.playBool02 = false;
        this.sliderTime = 0;
      }
    },
    // 当加载语音流元数据完成后，会触发该事件的回调函数
    // 语音元数据主要是语音的长度之类的数据
    onLoadedmetadata(res) {
      // console.log("22222s");
      // console.log(this.demo);
      // console.log(res);
      if (res.timeStamp != 0) {
        this.startPlay();
      }
      this.audio.waiting = false;
      // console.log(res.target.duration);
      // this.mp3MaxTime = parseInt(res.target.duration);
    },
    // 拖动跳转音频
    changeCurrentTime(index) {
      // // console.log(index);
      this.$refs.audio.currentTime = parseInt((index / 100) * this.mp3MaxTime);
    },
    // 静音切换
    startMutedOrNot() {
      this.$refs.audio.muted = !this.$refs.audio.muted;
      this.audio.muted = this.$refs.audio.muted;
    },
    // 音量控制
    format(val) {
      return "音量 : " + val;
    },
    // 音量改变
    changeVolume(index = 0) {
      this.$refs.audio.volume = index / 100;
      this.volume = index;
    },
    // 当音频开始等待
    onWaiting(res) {
      // console.log(res);
    }
  },
  filters: {
    formatSecond(second = 0) {
      return realFormatSecond(second);
    }
  }
};
</script>