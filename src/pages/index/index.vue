<script setup lang="ts">
import CustomNavbar from '@/pages/index/components/CustomNavbar.vue'
import { onLoad } from '@dcloudio/uni-app'
import { getHomeBannerApi } from '@/services/home'
import type { BannerItem } from '@/types/home'
import { ref } from 'vue'
import XtxSwiper from '@/components/XtxSwiper.vue'

const bannerList = ref<BannerItem[]>([])
const getHomeBannerData = async () => {
  const res = await getHomeBannerApi()
  bannerList.value = res.result
  console.log('列表' + res)
}
onLoad(() => {
  getHomeBannerData()
})
</script>

<template>
  <CustomNavbar />
  <XtxSwiper :list="bannerList" />
  <view class="index">index </view>
</template>

<style lang="scss">
//
</style>
