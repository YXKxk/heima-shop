<script setup lang="ts">
import CustomNavbar from '@/pages/index/components/CustomNavbar.vue'
import { onLoad } from '@dcloudio/uni-app'
import { getHomeBannerApI, getHomeCategoryAPI } from '@/services/home'
import type { BannerItem, CategoryItem } from '@/types/home'
import { ref } from 'vue'
import CategoryPanel from '@/pages/index/components/CategoryPanel.vue'

const bannerList = ref<BannerItem[]>([])
const getHomeBannerData = async () => {
  const res = await getHomeBannerApI()
  bannerList.value = res.result
}
const list = ref<CategoryItem[]>([])

//获取前台分类数据
const getHomeCategoryData = async () => {
  const res = await getHomeCategoryAPI()
  list.value = res.result
}
onLoad(() => {
  getHomeBannerData()
  getHomeCategoryData()
})
</script>

<template>
  <CustomNavbar />
  <XtxSwiper :list="bannerList" />
  <CategoryPanel :list="list" />
  <view class="index">index </view>
</template>

<style lang="scss">
page {
  background-color: #f7f7f7;
}
</style>
