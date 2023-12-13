<script setup>
import { onMounted, ref } from "vue";
import { shallowRef } from "@vue/reactivity";

import AMapLoader from "@amap/amap-jsapi-loader";
const map = shallowRef(null);

const initMap = () => {
  AMapLoader.load({
    key: "de4b8f2c272cf4dd9f94b4791f5325fd", // 申请好的Web端开发者Key，首次调用 load 时必填
    version: "2.0", // 指定要加载的 JSAPI 的版本，缺省时默认为 1.4.15
    plugins: [""], // 需要使用的的插件列表，如比例尺'AMap.Scale'等
  })
    .then((AMap) => {
      map = new AMap.Map("container", {
        //设置地图容器id
        viewMode: "3D", //是否为3D地图模式
        zoom: 5, //初始化地图级别
        center: [105.602725, 37.076636], //初始化地图中心点位置
      });
    })
    .catch((e) => {
      console.log(e);
    });
};

onMounted(() => {
  //DOM初始化完成进行地图初始化
  initMap();
});

// const count = ref(0);
</script>

<template>
  <div id="container"></div>
</template>

<style scoped>
#container {
  padding: 0px;
  margin: 0px;
  width: 100%;
  height: 800px;
}
</style>
