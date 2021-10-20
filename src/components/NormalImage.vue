<template>
  <div class="home">
    <el-image :src="src"/>
  </div>
</template>

<script>

export default {
  data () {
    return {
      // currentIndex: 1,
      src: null
    }
  },
  mounted () {
    // setInterval(() => {
    //   this.src = require(`@/assets/${this.currentIndex}.jpg`)
    //   this.currentIndex++
    //   if (this.currentIndex === 38) {
    //     this.currentIndex = 1
    //   }
    // }, 100)
  },
  methods: {
    change (imageName) {
      const context = require.context('@/assets/', false, /\.jpg$/) // 根据路径正则读取文件
      this.src = context(`./${imageName}.jpg`)
    }
  }
}
</script>
