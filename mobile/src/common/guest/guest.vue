<template>
  <div class="guests-box flexBox">
    <div class="guests-item" v-for="(item, index) in data" :key="index" @click="openLightBox(item)">
      <img :src="item.img" class="avatar" alt="">
      <h1>{{item.name}}</h1>
      <p>{{item.desc}}</p>
    </div>
    <!-- 灯箱 -->
    <div class="light-box" v-if="lightBox">
      <div class="light-box-main" >
        <div class="light-box-msg flexBox">
          <img alt="" :src="result.img">
          <div class="light-box-txt">
            <h1>姓名: <span class="name">{{result.name}}</span></h1>
            <p class="desc">简介：
              {{result.desc}}
            </p>
          </div>
        </div>
        <div class="light-box-tit flexBox">
          <h1>演讲主题</h1>
          <p>{{result.theme}}</p>
        </div>
        <a href="javascript:void(0);" class="light-box-close" @click="closeLightBox"></a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    data: {
      type: Array,
      default: () => []
    }
  },
  data () {
    return {
      lightBox: false,
      result: ""
    }
  },
  methods: {
    openLightBox(item) {
      this.result = item
      this.lightBox = true
    },
    closeLightBox () {
      this.result = ""
      this.lightBox = false
    }
  }
}
</script>


<style lang="stylus" scoped>
  .guests-box
    width 100%
    flex-flow wrap
    .guests-item
      flex 0 0 47%
      height 260px
      margin-right 20px
      background #e5e5e5
      margin-top 30px
      &:nth-child(2n)
        margin-right 0
      .avatar
        width 100px
        height 100px
        border-radius 100%
        background #fff
        margin 10px auto 15px
      h1
        font-size 16px
        font-weight normal
        text-align center
      p
        font-size .875rem /* 14/16 */
        height 70px
        margin 20px 10px 0
        overflow hidden
  .light-box
      position fixed
      left 0
      top 0
      width 100%
      height 100%
      z-index 1111
      background rgba(0,0,0,.5)
      .light-box-main
        width 92%
        height 370px
        padding 15px
        background #f9f9f9
        color #444
        border-radius 5px
        box-shadow 0 10px 25px rgba(0,0,0,.5)
        box-sizing border-box
        position absolute
        left 0
        top 0
        bottom 0
        right 0
        margin: auto
        .light-box-msg
          img
            width 120px
            height 120px
            border-radius 100%
        .light-box-txt
          flex 1
          margin-left 20px
          h1
            font-size .75rem /* 12/16 */
            font-weight 400
            line-height 40px
          p
            font-size .75rem /* 12/16 */
            max-height 260px
            line-height 24px
            overflow hidden
        .light-box-tit
          margin-top 10px
          h1
            font-size .875rem /* 14/16 */
            font-weight 400
      .light-box-close
        display block
        position: absolute
        top -12px
        right -12px
        width 30px
        height 30px
        cursor pointer
        z-index 8040
        border-radius 100%
        background #fff url(http://lib.albers.top/images/icon/close_bg.png) no-repeat
</style>
