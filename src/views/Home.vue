<template>
  <div class="container">
    <p class="description">
      {{ description }}
    </p>

    <div class="image-container">
      <buffered-image
        ref="bufferedImage"
        class="item"/>

      <normal-image
        ref="normalImage"
        class="item"/>
    </div>
  </div>
</template>

<script>
import NormalImage from '../components/NormalImage'
import BufferedImage from '@/components/BufferedImage'

export default {
  components: {
    NormalImage,
    BufferedImage
  },
  data () {
    return {
      currentIndex: 1,
      description: '',
      intervalMs: 50
    }
  },
  mounted () {
    setInterval(() => {
      if (this.$refs.bufferedImage.change(this.currentIndex)) {
        this.description = `当前图片：${this.currentIndex}.jpg，切换间隔：${this.intervalMs}ms`
        this.$refs.normalImage.change(this.currentIndex)
        this.currentIndex++
      }
      if (this.currentIndex === 38) {
        this.currentIndex = 1
      }
    }, this.intervalMs)
  }
}
</script>

<style lang="scss" scoped>
.container {
  display: flex;
  flex-direction: column;

  .description {
    width: 400px;
    text-align: center;
  }

  .image-container {
    display: flex;

    .item {
      width: 200px;
      height: 200px;
    }
  }
}
</style>
