<template>
  <div ref="wrap" class="wrap">
    <div ref="content" class="content" :class="animationClass" :style="contentStyle" @animationend="onAnimationEnd"
      @webkitAnimationEnd="onAnimationEnd">
      <slot></slot>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      content: {
        default: ''
      },
      delay: {
        type: Number,
        default: 0.5
      },
      speed: {
        type: Number,
        default: 100
      }
    },
    mounted() {},
    data() {
      return {
        wrapWidth: 0,
        firstRound: true,
        duration: 0,
        offsetWidth: 0,
        animationClass: '',
      };
    },
    computed: {
      contentStyle() {
        return {
          paddingLeft: (this.firstRound ? 0 : this.wrapWidth) + 'px',
          animationDelay: (this.firstRound ? this.delay : 0) + 's',
          animationDuration: this.duration + 's'
        };
      }
    },
    watch: {
      content: {
        handler() {
          this.$nextTick(() => {
            const {
              wrap,
              content
            } = this.$refs;
            const wrapWidth = wrap.getBoundingClientRect().width;
            const offsetWidth = content.getBoundingClientRect().width;
            this.wrapWidth = wrapWidth;
            this.offsetWidth = offsetWidth;
            this.duration = offsetWidth / this.speed;
            this.animationClass = 'animate';
          });
        }
      }
    },
    methods: {
      onAnimationEnd() {
        this.firstRound = false
        this.duration = (this.offsetWidth + this.wrapWidth) / this.speed;
        this.animationClass = "animate-infinite";
      }
    }
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .wrap {
    width: 100%;
    height: 30px;
    line-height: 30px;
    overflow: hidden;
    position: relative;
    background: rgba(0, 0, 0, 0.5);
    position: relative;
    padding: 0;
    color: #fff;
  }

  .wrap .content {
    position: absolute;
    white-space: nowrap;
  }

  .animate {
    animation: paomadeng linear;
  }

  .animate-infinite {
    animation: paomadeng-infinite linear infinite;
  }

  @keyframes paomadeng {
    to {
      transform: translate3d(-100%, 0, 0);
    }
  }

  @keyframes paomadeng-infinite {
    to {
      transform: translate3d(-100%, 0, 0);
    }
  }
</style>