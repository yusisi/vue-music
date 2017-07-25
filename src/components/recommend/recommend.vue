<template>
  <div class="recommend">
      <div class="recommend-content">
          <div v-if="recommends.length" rel="slideWrapper" class="slider-wrapper">
              <slider>
                  <div v-for="item in recommends">
                        <a :href="item .linkUrl">
                            <img class="needsclick" :src="item.picUrl" @load="loadImage" alt="">
                        </a>
                  </div>
              </slider>
          </div>
          <div class="recommend-list">
              <h1></h1>
              <ul></ul>
          </div>
      </div>
  </div>
</template>

<script type="text/ecmascript-6">
import Slider from 'base/alider/slider'
import {getRecommend} from 'api/recommend'
import {ERR_OK} from 'api/config'
export default {
    data() {
        return {
            recommends: []
        }
    },
    created() {
        this._getRecommend()
    },
    methods: {
        _getRecommend() {
            getRecommend().then((res) => {
                if (res.code === ERR_OK) {
                    this.recommends = res.data.slider
                }
            })
        }
    }
}
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">

</style>