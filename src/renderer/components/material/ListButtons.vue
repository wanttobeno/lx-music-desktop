<template lang="pug">
div(:class="$style.btns")
  button(type="button" v-if="playBtn" title="播放" @click.stop="handleClick('play')")
    svg(version='1.1' xmlns='http://www.w3.org/2000/svg' xlink='http://www.w3.org/1999/xlink' height='100%' viewBox='0 0 287.386 287.386' space='preserve')
      use(xlink:href='#icon-testPlay')
  button(type="button" v-if="downloadBtn" title="下载" @click.stop="handleClick('download')")
    svg(version='1.1' xmlns='http://www.w3.org/2000/svg' xlink='http://www.w3.org/1999/xlink' height='100%' viewBox='0 0 475.078 475.077' space='preserve')
      use(xlink:href='#icon-download')
  button(type="button" title="添加" v-if="userInfo" @click.stop="handleClick('add')")
    svg(version='1.1' xmlns='http://www.w3.org/2000/svg' xlink='http://www.w3.org/1999/xlink' height='100%' viewBox='0 0 42 42' space='preserve')
      use(xlink:href='#icon-addTo')
  button(type="button" v-if="startBtn" title="开始" @click.stop="handleClick('start')")
    svg(version='1.1' xmlns='http://www.w3.org/2000/svg' xlink='http://www.w3.org/1999/xlink' height='100%' viewBox='0 0 170 170' space='preserve')
      use(xlink:href='#icon-play')
  button(type="button" v-if="pauseBtn" title="暂停" @click.stop="handleClick('pause')")
    svg(version='1.1' xmlns='http://www.w3.org/2000/svg' xlink='http://www.w3.org/1999/xlink' height='100%' viewBox='0 0 277.338 277.338' space='preserve')
      use(xlink:href='#icon-pause')
  button(type="button" v-if="fileBtn" title="定位文件" @click.stop="handleClick('file')")
    svg(version='1.1' xmlns='http://www.w3.org/2000/svg' xlink='http://www.w3.org/1999/xlink' height='100%' viewBox='-61 0 512 512' space='preserve')
      use(xlink:href='#icon-musicFile')
  button(type="button" v-if="removeBtn" title="移除" @click.stop="handleClick('remove')")
    svg(version='1.1' xmlns='http://www.w3.org/2000/svg' xlink='http://www.w3.org/1999/xlink' height='100%' viewBox='0 0 212.982 212.982' space='preserve')
      use(xlink:href='#icon-delete')
  button(type="button" v-if="searchBtn" title="搜索" @click.stop="handleClick('search')")
    svg(version='1.1' xmlns='http://www.w3.org/2000/svg' xlink='http://www.w3.org/1999/xlink' height='100%' viewBox='0 0 30.239 30.239' space='preserve')
      use(xlink:href='#icon-search')

</template>

<script>
import { mapGetters } from 'vuex'

export default {
  props: {
    index: {
      type: Number,
      required: true,
    },
    startBtn: {
      type: Boolean,
      default: false,
    },
    pauseBtn: {
      type: Boolean,
      default: false,
    },
    removeBtn: {
      type: Boolean,
      default: true,
    },
    downloadBtn: {
      type: Boolean,
      default: true,
    },
    playBtn: {
      type: Boolean,
      default: true,
    },
    searchBtn: {
      type: Boolean,
      default: false,
    },
    fileBtn: {
      type: Boolean,
      default: false,
    },
  },
  computed: {
    ...mapGetters(['userInfo']),
  },
  methods: {
    handleClick(action) {
      this.$emit('btn-click', { action, index: this.index })
    },
  },
}
</script>


<style lang="less" module>
@import '../../assets/styles/layout.less';

.btns {
  button {
    background-color: transparent;
    border: none;
    border-radius: 3px;
    margin-right: 5px;
    cursor: pointer;
    padding: 4px 7px;
    color: @color-btn;
    outline: none;
    transition: background-color 0.2s ease;
    line-height: 0;
    &:last-child {
      margin-right: 0;
    }

    svg {
      height: 1.2em;
    }

    &:hover {
      background-color: @color-theme_2-hover;
    }
    &:active {
      background-color: @color-theme_2-active;
    }
  }
}

each(@themes, {
  :global(#container.@{value}) {
    .btns {
      button {
        color: ~'@{color-@{value}-btn}';
        &:hover {
          background-color: ~'@{color-@{value}-theme_2-hover}';
        }
        &:active {
          background-color: ~'@{color-@{value}-theme_2-active}';
        }
      }
    }
  }
})
</style>
